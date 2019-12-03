<template>
  <div id="app">
    <router-view></router-view>
    <MainTapBar></MainTapBar>
  </div>
</template>

<script>
import MainTapBar from './components/common/tapbar/mainTapbar'
export default {
  name: 'app',
  data () {
    return {
    }
  },
  components: {
    MainTapBar
  }
}
</script>

<style>
@import "assets/css/base.css";
</style>
