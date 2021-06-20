<template>
  <div>
    <!-- 普通使用方式 -->
    <image-wrapper :src="imageSrc">
      <span slot="desc">{{ context }}</span>
    </image-wrapper>
    <div class="line">
      <Canvas ref="line01" v-bind:width="canvasWidth" v-bind:height="canvasHeight"></Canvas>
      <div style="display:none">
        <img id="sm" ref="line02" src="@/components/Imageswpper/bloSin.png" />
      </div>
    </div>
  </div>
</template>
<script>
import ImageWrapper from '@/components/Imageswpper/index.vue'

export default {
  // 引入组件
  components: {
    ImageWrapper
  },
  data () {
    return {
      canvasWidth: 600,
      canvasHeight: 400,
      ctx: null,
      context: '菠萝星系',
      imageSrc: require('@/components/Imageswpper/bloSin.png')
    }
  },
  mounted () {
    this.init()
  },
  methods: {
    init: function () {
      console.log(this.$refs)
      this.ctx = this.$refs.line01.getContext('2d')
      this.img = document.getElementById('sm')
      this.ctx.drawImage(this.img, 10, 10)
      this.draw()
    },
    draw: function () {}
  }
}
</script>
<style>
.line canvas {
  border: 1px solid red;
}
</style>
