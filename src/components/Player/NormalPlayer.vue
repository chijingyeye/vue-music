<template>
  <transition
    :css="false"
    @enter="enter"
    @leave="leave">
    <div class="normal-player" v-show="this.isFullScreen" ref="normalPlayer">
      <div class="player-wrapper">
        <PlayerHeader></PlayerHeader>
        <PlayerMiddle></PlayerMiddle>
        <PlayerBottom></PlayerBottom>
      </div>
      <div class="player-bg">
        <img src="https://p1.music.126.net/qpvBqYIqkRhO9Ry2qOCdJQ==/2942293117852634.jpg" alt="">
      </div>
    </div>
  </transition>
</template>

<script>
import PlayerHeader from './PlayerHeader'
import PlayerMiddle from './PlayerMiddle'
import PlayerBottom from './PlayerBottom'
import { mapGetters } from 'vuex'
import Velocity from 'velocity-animate'
import 'velocity-animate/velocity.ui'

export default {
  name: 'NormalPlayer',
  components: {
    PlayerHeader,
    PlayerMiddle,
    PlayerBottom
  },
  methods: {
    enter (el, done) {
      Velocity(el, 'transition.shrinkIn', { duration: 500 }, function () {
        done()
      })
    },
    leave (el, done) {
      Velocity(el, 'transition.shrinkOut', { duration: 500 }, function () {
        done()
      })
    }
  },
  computed: {
    ...mapGetters([
      'isFullScreen'
    ])
  }
}
</script>

<style scoped lang="scss">
@import "../../assets/css/variable";
@import "../../assets/css/mixin";
.normal-player {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: pink;
  @include bg_sub_color();
  .player-wrapper {
    width: 100%;
    height: 100%;
    position: relative;
    z-index: 99;
  }
  .player-bg {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    img {
      margin: 0 auto;
      height: 100%;
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%,-50%);
      filter: blur(10px);
    }
  }
}
</style>
