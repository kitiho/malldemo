<template>
  <swiper
    :options="swiperOption"
    ref="mySwiper"
    @someSwiperEvent="callback"
  >
    <swiper-slide
      v-for="item in homebanners"
      :key="item.index"
    >
      <a :href="item.link">
        <img
          :src="item.image"
          alt=""
        >
      </a>
    </swiper-slide>
    <div
      class="swiper-pagination"
      slot="pagination"
    ></div>
  </swiper>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name: 'carrousel',
  components: {
    swiper,
    swiperSlide
  },
  props: {
    homebanners: []
  },
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination',
          dynamicBullets: true
        },
        autoplay: {
          delay: 2500,
          disableOnInteraction: false
        }
      }
    }
  },
  computed: {
    swiper () {
      return this.$refs.mySwiper.swiper
    }
  },
  mounted () {
    // current swiper instance
    // 然后你就可以使用当前上下文内的swiper对象去做你想做的事了
    console.log('this is current swiper instance object', this.swiper)
    this.swiper.slideTo(3, 1000, false)
  }
}
</script>
<style scoped>
img {
  width: 100%;
}
</style>
