<template>
  <swiper ref="mySwiper" :options="swiperOptions" class="banner">
    <swiper-slide class="cd">
      <div class="cd-wrapper">
        <img src="https://p1.music.126.net/qpvBqYIqkRhO9Ry2qOCdJQ==/2942293117852634.jpg" alt="">
      </div>
      <p>简单点 说话的方式简单点</p>
    </swiper-slide>
    <swiper-slide class="lyric">
      <ScrollView>
        <ul>
          <li>我是第1个li</li>
          <li>我是第2个li</li>
          <li>我是第3个li</li>
          <li>我是第4个li</li>
          <li>我是第5个li</li>
          <li>我是第6个li</li>
          <li>我是第7个li</li>
          <li>我是第8个li</li>
          <li>我是第9个li</li>
          <li>我是第10个li</li>
          <li>我是第11个li</li>
          <li>我是第12个li</li>
          <li>我是第13个li</li>
          <li>我是第14个li</li>
          <li>我是第15个li</li>
          <li>我是第16个li</li>
          <li>我是第17个li</li>
          <li>我是第18个li</li>
          <li>我是第19个li</li>
          <li>我是第20个li</li>
          <li>我是第21个li</li>
          <li>我是第22个li</li>
          <li>我是第23个li</li>
          <li>我是第24个li</li>
          <li>我是第25个li</li>
          <li>我是第26个li</li>
          <li>我是第27个li</li>
          <li>我是第28个li</li>
          <li>我是第29个li</li>
          <li>我是第30个li</li>
          <li>我是第31个li</li>
          <li>我是第32个li</li>
          <li>我是第33个li</li>
          <li>我是第34个li</li>
          <li>我是第35个li</li>
          <li>我是第36个li</li>
          <li>我是第37个li</li>
          <li>我是第38个li</li>
          <li>我是第39个li</li>
          <li>我是第40个li</li>
          <li>我是第41个li</li>
          <li>我是第42个li</li>
          <li>我是第43个li</li>
          <li>我是第44个li</li>
          <li>我是第45个li</li>
          <li>我是第46个li</li>
          <li>我是第47个li</li>
          <li>我是第48个li</li>
          <li>我是第49个li</li>
          <li>我是第50个li</li>
        </ul>
      </ScrollView>
    </swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
</template>

<script>
import 'swiper/css/swiper.css'
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import ScrollView from '../../components/ScrollView'

export default {
  name: 'PlayerMiddle',
  data () {
    return {
      swiperOptions: {
        // loop: true,
        // autoplay: {
        //   delay: 3000,
        //   stopOnLastSlide: false,
        //   disableOnInteraction: true
        // },
        observer: true,
        observeParents: true,
        observeSlideChildren: true,
        pagination: {
          el: '.swiper-pagination',
          bulletClass: 'my-bullet',
          bulletActiveClass: 'my-bullet-active'
        }
      }
    }
  },
  components: {
    Swiper,
    SwiperSlide,
    ScrollView
  },
  directives: {
    swiper: directive
  }
}
</script>

<style scoped lang="scss">
@import "../../assets/css/variable";
@import "../../assets/css/mixin";
.banner {
  position: fixed;
  top: 150px;
  bottom: 250px;
  left: 0;
  right: 0;
  .cd {
    .cd-wrapper {
      width: 500px;
      height: 500px;
      overflow: hidden;
      border-radius: 50%;
      border: 15px solid #fff;
      position: relative;
      margin: 40px auto 0;
      animation: sport 15s linear infinite;
      animation-play-state: paused;
      &.active {
        animation-play-state: running
      ;
      }
      img {
        width: 100%;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%,-50%);
      }
    }
    p {
      @include font_size($font_medium);
      @include font_color();
      text-align: center;
      margin-top: 50px;
    }
  }
  .lyric {
    padding-bottom: 100px;
    li {
      text-align: center;
      @include font_size($font_medium);
      @include font_color();
      margin: 20px 0;
      &:last-of-type {
        padding-bottom: 100px;
      }
    }
  }
}
@keyframes sport {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
<style lang="scss">
@import "../../assets/css/variable";
@import "../../assets/css/mixin";
.my-bullet {
  display: inline-block;
  width: 16px;
  height: 16px;
  border-radius: 10px;
  background: #fff;
  margin: 0 10px;
}
.my-bullet-active {
  @include bg_color();
  width: 40px;
}
</style>
