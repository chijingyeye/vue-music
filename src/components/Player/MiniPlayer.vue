<template>
  <transition
    :css="false"
    @enter="enter"
    @leave="leave">
    <div class="mini-player" v-show="this.isShowMiniPlayer">
      <div class="player-wrapper">
        <div class="player-left" @click="showNormalPlayer">
          <img src="https://p1.music.126.net/qpvBqYIqkRhO9Ry2qOCdJQ==/2942293117852634.jpg" alt="">
          <div class="player-title">
            <h3>演员</h3>
            <p>薛之谦</p>
          </div>
        </div>
        <div class="player-right">
          <div class="play" @click="play" ref="play"></div>
          <div class="list" @click.stop="showList"></div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import Velocity from 'velocity-animate'
import 'velocity-animate/velocity.ui'
import {
  mapActions,
  mapGetters
} from 'vuex'

export default {
  name: 'MiniPlayer',
  computed: {
    ...mapGetters([
      'isShowMiniPlayer',
      'isPlaying'
    ])
  },
  methods: {
    ...mapActions([
      'setFullScreen',
      'setMiniPlayer',
      'setIsPlaying'
    ]),
    showList () {
      this.$emit('showList')
    },
    showNormalPlayer () {
      this.setFullScreen(true)
      this.setMiniPlayer(false)
    },
    enter (el, done) {
      Velocity(el, 'transition.bounceUpIn', { duration: 500 }, function () {
        done()
      })
    },
    leave (el, done) {
      Velocity(el, 'transition.bounceDownOut', { duration: 500 }, function () {
        done()
      })
    },
    play () {
      this.setIsPlaying(!this.isPlaying)
    }
  },
  watch: {
    isPlaying (newvalue, oldvalue) {
      if (newvalue) {
        this.$refs.play.classList.add('active')
      } else {
        this.$refs.play.classList.remove('active')
      }
    }
  }
}
</script>

<style scoped lang="scss">
@import "../../assets/css/variable";
@import "../../assets/css/mixin";
.mini-player {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 150px;
  .player-wrapper {
    width: 100%;
    height: 100%;
    @include bg_color();
    display: flex;
    align-items: center;
    justify-content: space-between;
    .player-left {
      display: flex;
      padding-left: 20px;
      img {
        width: 100px;
        height: 100px;
        border-radius: 50%;
        margin-right: 20px;
      }
      .player-title {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        h3 {
          @include font_size($font_medium);
          color: #ffffff;
        }
        p {
          @include font_size($font_medium_s);
          color: #ffffff;
          margin-top: 10px;
        }
      }
    }
    .player-right {
      display: flex;
      align-items: center;
      .play {
        width: 80px;
        height: 80px;
        @include bg_img('../../assets/images/pause');
        &.active {
          @include bg_img('../../assets/images/play')
        }
      }
      .list {
        width: 120px;
        height: 120px;
        @include bg_img('../../assets/images/list')
      }
    }
  }
}
</style>
