<template lang="pug">
.hero
  .left
    h1 All in one DEX
    p.desc
      | Alcor is a lego of decentralized finance built on multi-chain, and a
      | provider of solutions in one tap.
    .actions
      alcor-link.start(to='/markets')
        | Start Trading
      alcor-button(@click="openInNewTab('https://docs.alcor.exchange/')")
        | Read docs
  .right
    circles(v-if='canShowCircles')
</template>

<script>
import AlcorLink from '@/components/AlcorLink'
import AlcorButton from '@/components/AlcorButton'
import Circles from '@/components/landing/Circles'

export default {
  name: 'Hero',
  components: {
    AlcorLink,
    AlcorButton,
    Circles
  },
  computed: {
    canShowCircles() {
      return !this.$device.isAndroid
    }
  }
}
</script>

<style lang="scss" scoped>
.hero {
  height: 340px;
  display: flex;
  flex-wrap: wrap;
  position: relative;
}

.left {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
  width: 50%;
  position: relative;
  z-index: 2;
}

h1 {
  font-size: 3rem;
}

.desc {
  width: 100%;
  max-width: 360px;
}

.actions {
  margin-top: 20px;

  &>* {
    padding: 6px 20px !important;
  }

  .start {
    margin-right: 15px;
    background: var(--main-green);
    color: white !important;

    &:hover {
      opacity: 0.8;
    }
  }
}

.theme-dark .actions {
  .start {
    background: var(--btn-active);
    color: var(--main-green) !important;
  }
}

.right {
  position: relative;
  width: 50%;
  height: 100%;
  z-index: 0;
}

.frame {
  position: absolute;
  pointer-events: none;

  top: -100%;
  right: -50%;
}

.frame_logo {
  position: absolute;
  top: 60%;
  left: 40%;
}

@media only screen and (max-width: 1040px) {
  .frame {
    right: -40%;
  }
}

@media only screen and (max-width: 840px) {

  .left,
  .right {
    width: 100%;
  }

  .right {
    position: absolute;
    opacity: 0.4;
  }

  .frame {
    right: 50%;
    transform: translate(50%, -50%);
  }

}
</style>
