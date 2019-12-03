<template>
  <div
    class="tap-bar-item"
    @click="itemClick"
  >
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>

    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>
  </div>

</template>

<script>
export default {
  name: 'TapBarItem',
  props: {
    path: String,
    activeColor: {
      default: 'red',
      type: String
    }
  },
  data () {
    return {
    }
  },
  computed: {
    isActive () {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle () {
      return this.isActive ? { color: this.activeColor } : {}
    }
  },
  methods: {
    itemClick () {
      if (this.$route.path !== this.path) {
        this.$router.replace(this.path)
      }
    }
  }
}
</script>

<style>
.tap-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}
.tap-bar-item img {
  margin-top: 5px;
  width: 25px;
  height: 25px;
}
.active {
  color: red;
}
</style>
