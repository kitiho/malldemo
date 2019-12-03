<template>
  <tap-bar>
    <tap-bar-item
      path="/home"
      activeColor="#db639b"
    >
      <img
        src="../../../assets\img\tapbar\主页.svg"
        alt=""
        slot="item-icon"
      >
      <img
        src="../../../assets\img\tapbar\主页_active.svg"
        alt=""
        slot="item-icon-active"
      >
      <div slot="item-text">主页</div>
    </tap-bar-item>
    <tap-bar-item
      path="/category"
      activeColor="#db639b"
    >
      <img
        src="../../../assets\img\tapbar\分类.svg"
        alt=""
        slot="item-icon"
      >
      <img
        src="../../../assets\img\tapbar\分类_active.svg"
        alt=""
        slot="item-icon-active"
      >
      <div slot="item-text">分类</div>
    </tap-bar-item>
    <tap-bar-item
      path="/cart"
      activeColor="#db639b"
    >
      <img
        src="../../../assets\img\tapbar\购物车.svg"
        alt=""
        slot="item-icon"
      >
      <img
        src="../../../assets\img\tapbar\购物车_active.svg"
        alt=""
        slot="item-icon-active"
      >
      <div slot="item-text">购物车</div>
    </tap-bar-item>
    <tap-bar-item
      path="/profile"
      activeColor="#db639b"
    >
      <img
        src="../../../assets\img\tapbar\我的.svg"
        alt=""
        slot="item-icon"
      >
      <img
        src="../../../assets/img/tapbar/我的_active.svg"
        alt=""
        slot="item-icon-active"
      >
      <div slot="item-text">我的</div>
    </tap-bar-item>
  </tap-bar>
</template>

<script>
import TapBar from './TapBar'
import TapBarItem from './TapBarItem'
export default {
  components: {
    TapBar,
    TapBarItem
  }
}
</script>

<style>
</style>
