<template>
  <div class="TapControl">
    <div
      v-for="(item, index) in titles"
      :key="index"
      class="TapControl-item"
      @click="itemClick(index)"
    >
      <span :class="{active:currentIndex==index}">{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TapControl',
  props: {
    titles: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      currentIndex: 0
    }
  },
  methods: {
    itemClick (index) {
      this.currentIndex = index
      this.$emit('tapClick', index)
    }
  },
}
</script>

<style>
.TapControl {
  display: flex;
  text-align: center;
  font-size: 15px;
  height: 40px;
  line-height: 40px;
  background-color: #fff;
}
.TapControl-item {
  flex: 1;
}
.active {
  color: #db639b;
  border-bottom: 3px solid #db639b;
  padding-bottom: 5px;
}
</style>
