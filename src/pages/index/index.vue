<template>
  <view class="index">
    <scroll-view scrollY class="parent-scroll" @scroll="handleScroll">
      <scroll-view scrollY @scroll.stop="handleChildScroll" class="child-scroll">
        <view :key="item" v-for="item in 20">
          {{item}}
        </view>
      </scroll-view>
    </scroll-view>
  </view>
</template>

<script>
import { reactive, toRefs } from 'vue';
export default {
  name: 'Index',
  setup() {
    const handleScroll = (ev) => {
      console.log('parent scroll', ev)
    };

    const handleChildScroll = (ev) => {
      ev.stopPropagation()
      console.log('child scroll: ', ev)
    }

    return {
      handleScroll,
      handleChildScroll
    }
  }
}
</script>

<style lang="scss">
.index {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

  .parent-scroll {
    height: 100vh;
  }
  .child-scroll {
    height: 200px;
  }
}
</style>
