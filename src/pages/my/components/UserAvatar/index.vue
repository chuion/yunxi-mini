<template>
  <div class="user-avatar">
    <div class="user-avatar__name" :style="style">
      {{ name }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'

const userInfo = ref({
  name: '张三',
  userId: 'user342nf9r32jf239c'
})

const name = computed(() => userInfo.value.name)

const style = computed(() => {
  const colorList = [
    'linear-gradient(0.91deg, #3A66E7 3.86%, rgba(58, 102, 231, 0.53) 100.78%)', // 蓝色
    'linear-gradient(180deg, rgba(121, 62, 245, 0.53) 0%, #793EF5 100%)', // 紫色
    'linear-gradient(90deg, #E52D27 0%, #B31217 100%)', // 红色
    'linear-gradient(0deg, #57BEA8 -1.56%, #65D6BD 100%)' // 绿色
  ]
  const idLen = userInfo.value.userId.length
  const idMarker = userInfo.value.userId.slice(idLen - 4, idLen)
  const colorIndex = parseInt(idMarker, 16) % 4

  return {
    background: colorList[colorIndex]
  }
})
</script>

<style lang="scss" scoped>
.user-avatar {
  position: relative;
  // width: 32px;
  // height: 32px;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  flex: 0 0 auto;

  &__name {
    width: 100%;
    height: 100%;
    font-size: 18px;
    text-align: center;
    line-height: 32px;
    color: #fff;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &__frame {
    // width: 38px !important;
    // height: 38px;
    width: 100%;
    height: 100%;

    position: absolute;
    top: 0;
    left: 0;
  }
}
</style>
