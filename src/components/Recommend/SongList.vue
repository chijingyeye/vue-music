<template>
<div class="song">
  <div class="song-top">
    <h3>{{ title }}</h3>
  </div>
  <ul class="song-list">
    <li v-for="value in songs" :key="value.id" class="item" @click="selectMusic">
      <img v-lazy="value.picUrl" alt="">
      <div>
        <h3>{{ value.name }}</h3>
        <p>{{ value.song.artists[0].name }}</p>
      </div>
    </li>
  </ul>
</div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'SongList',
  props: {
    songs: {
      type: Array,
      default: () => [],
      required: true
    },
    title: {
      type: String,
      default: () => [],
      required: true
    }
  },
  methods: {
    ...mapActions([
      'setFullScreen'
    ]),
    selectMusic () {
      this.setFullScreen(true)
    }
  }
}
</script>

<style scoped lang="scss">
@import '../../assets/css/mixin';
@import '../../assets/css/variable';
.song {
  width: 100%;
  @include bg_sub_color();
  .song-top {
    width: 100%;
    height: 84px;
    line-height: 84px;
    @include bg_sub_color();
    padding: 0 20px;
    h3 {
      @include font_size($font_large);
      font-weight: bold;
      @include font_color();
    }
  }
  .song-list {
    width: 100%;
    overflow: hidden;
    .item {
      width: 100%;
      display: flex;
      align-items: center;
      padding: 0 20px;
      margin-bottom: 20px;
      img {
        width: 100px;
        height: 100px;
        border-radius: 20px;
        margin-right: 20px;
      }
      div {
        h3 {
          @include font_size($font_medium);
          @include font_color();
        }
        p {
          @include font_size($font_samll);
          @include font_color();
          opacity: 0.6;
          margin-top: 10px;
        }
      }
    }
  }
}
</style>
