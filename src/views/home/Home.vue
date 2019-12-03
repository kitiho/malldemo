<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <swiper :homebanners="banners"></swiper>
    <recommend :recommends="recommends"></recommend>
    <feature-view></feature-view>
    <TapControl
      :titles="['流行','新款','精选']"
      class="tapbar-control"
      @tapClick="tapClick"
    ></TapControl>
    <GoodsList :goods="showGoods"></GoodsList>
  </div>

</template>

<script>
import NavBar from '../../components/common/navbar/NavBar'
import Swiper from '../../components/common/swiper/Swiper'

import Recommend from '../home/childComps/RecommendView'
import FeatureView from '../home/childComps/FeatureView'

import TapControl from '../../components/content/TapControl'
import GoodsList from '../../components/content/goods/GoodsList'

import { getHomeMultidata, getHomeGoods } from '../../network/home'
export default {
  name: 'Home',
  components: {
    NavBar,
    Swiper,
    Recommend,
    FeatureView,
    TapControl,
    GoodsList
  },
  data () {
    return {
      demo: '111',
      result: null,
      banners: [],
      recommends: [],
      goods: {
        'pop': { page: 0, list: [] },
        'new': { page: 0, list: [] },
        'sell': { page: 0, list: [] }
      },
      currentType: 'pop'
    }
  },
  computed: {
    showGoods () {
      return this.goods[this.currentType].list
    }
  },
  created () {
    this.getHomeMultidata()
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  methods: {
    /*
  事件监听相关
  */
    tapClick (index) {
      switch (index) {
        case 0:
          this.currentType = 'pop'
          break;
        case 1:
          this.currentType = 'new'
          break;
        case 2:
          this.currentType = 'sell'
          break;
      }
    },
    /*
    网络请求相关
    */
    getHomeMultidata () {
      getHomeMultidata().then(res => {
        this.result = res
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend.list
      })
    },
    getHomeGoods (type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type, page).then(res => {
        this.goods[type].list.push(...res.data.list)
        this.goods[type].page += 1
      })
    },

  },
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
  top: 0;
  left: 0;
  right: 0;
  z-index: 8;
}
.tapbar-control {
  position: sticky;
  top: 44px;
  z-index: 9;
}
</style>
