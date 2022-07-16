<template>
  <div class="detail-top">
    <div class="img-container">
      <img :src="path" alt="">
      <div class="mask" ref="mask"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailTop',
  methods: {
    changeMask (opacity) {
      this.$refs.mask.style.opacity = opacity
    }
  },
  props: {
    path: {
      type: String,
      default: '',
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
.detail-top {
  width: 100%;
  height: 500px;
  overflow: hidden;
  img {
    width: 100%;
  }
  .mask {
    position: absolute;
    width: 100%;
    height: 100%;
    background: #000000;
    left: 0;
    top: 0;
    opacity: 0.5;
  }
}
</style>
