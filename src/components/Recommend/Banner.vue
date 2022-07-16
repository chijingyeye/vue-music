<template>
  <swiper ref="mySwiper" :options="swiperOptions" class="banner" v-if="banners.length > 0">
    <swiper-slide v-for="value in banners" :key="value.bannerId" class="item">
      <a :href="value.url">
        <img :src="value.pic" :alt="value.typeTitle">
      </a>
    </swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
</template>

<script>
import 'swiper/css/swiper.css'
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'

export default {
  name: 'Banner',
  data () {
    return {
      swiperOptions: {
        loop: true,
        autoplay: {
          delay: 3000,
          stopOnLastSlide: false,
          disableOnInteraction: true
        },
        observer: true,
        observeParents: true,
        observeSlideChildren: true,
        pagination: {
          el: '.swiper-pagination'
        }
      }
    }
  },
  props: {
    banners: {
      type: Array,
      default: () => [],
      required: true
    }
  },
  components: {
    Swiper,
    SwiperSlide
  },
  directives: {
    swiper: directive
  }
}
</script>

<style scoped lang="scss">
.banner {
  .item {
    width: 100%;
    img {
      width: 100%;
    }
  }
}
</style>
<style lang="scss">
@import "../../assets/css/mixin";
.banner {
  .swiper-pagination-bullet {
    width: 16px;
    height: 16px;
    background: #ffffff;
    opacity: 1;
    margin: 0 6px !important;
  }
  .swiper-pagination-bullet-active {
    @include bg_color()
  }
}
</style>
