<template>
  <view
    class="custom-nav"
    :style="{
      height: navHeight + 'px',
      'padding-top': statusBarHeight + 'px'
    }"
  >
    <text>{{ title }}</text>
  </view>
</template>

<script setup lang="ts">
import { onLoad } from '@dcloudio/uni-app'
import { ref } from 'vue'

const navHeight = ref()
const statusBarHeight = ref()

onLoad(() => {
  // 获取手机系统的信息（在这主要是获取状态栏和胶囊的高度）
  const config = uni.getSystemInfoSync()
  statusBarHeight.value = config.statusBarHeight
  navHeight.value =
    statusBarHeight.value + (config.system.indexOf('iOS') > -1 ? 44 : 48)
})

defineProps({
  title: {
    type: String,
    default: ''
  }
})
</script>

<style lang="scss" scoped>
.custom-nav {
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 500;
  font-size: 34rpx;
  line-height: 48rpx;
}
</style>
