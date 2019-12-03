<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <swiper :homebanners="banners"></swiper>
    <recommend :recommends="recommends"></recommend>
    <feature-view></feature-view>
  </div>
</template>

<script>
import NavBar from '../../components/common/navbar/NavBar'
import Swiper from '../../components/common/swiper/Swiper'
import Recommend from '../home/childComps/RecommendView'
import FeatureView from '../home/childComps/FeatureView'

import { getHomeMultidata } from '../../network/home'
export default {
  name: 'Home',
  components: {
    NavBar,
    Swiper,
    Recommend,
    FeatureView
  },
  data () {
    return {
      demo: '111',
      result: null,
      banners: [],
      recommends: []
    }
  },
  created () {
    getHomeMultidata().then(res => {
      this.result = res
      this.banners = res.data.banner.list
      this.recommends = res.data.recommend.list
    })
  }
}
</script>

<style>
#home {
  padding-top: 44px;
}
.home-nav {
  background-color: #db639b;
  color: #fff;
  position: fixed;
  top:0;
  left: 0;
  right: 0;
  z-index: 8;
}
</style>
