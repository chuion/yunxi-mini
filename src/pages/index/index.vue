<template>
  <view class="index-page">
    <u-image width="100%" height="600rpx" :src="imageUrl"></u-image>

    <view class="index-page__main">
      <view class="yx-card">
        <u-image
          width="100%"
          height="200rpx"
          mode="aspectFit"
          src="/static/images/logo.jpg"
        ></u-image>
        <view class="link">了解更多</view>
      </view>
      <view class="yx-card people-area" style="margin-top: 20rpx">
        <view class="people-card">
          <text>设计师作品</text>
          <u-icon name="level" color="orange" size="100"></u-icon>
        </view>
        <view class="divider"></view>
        <view class="people-card">
          <text>促销活动</text>
          <u-icon name="tags" color="orange" size="100"></u-icon>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
const imageUrl =
  'https://cdn.stocksnap.io/img-thumbs/960w/home-office_TTSZNHYKJD.jpg'
</script>

<style lang="scss" scoped>
.index-page {
  width: 100vw;
  height: 100vh;

  &__main {
    width: 100%;
    padding: 20rpx;
    position: relative;
    top: -100rpx;
  }

  .yx-card {
    background-color: #fff;
    border-bottom: 4rpx solid orange;
    padding: 40rpx;
    box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.08);
    border-radius: 8rpx;
  }

  .link {
    background: orange;
    border-radius: 40rpx;
    width: 160rpx;
    margin: 0 auto;
    margin-top: 20rpx;
    color: #fff;
    text-align: center;
  }

  .people-area {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 40rpx;

    .people-card {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 0 40rpx;
    }

    .divider {
      width: 2rpx;
      height: 140rpx;
      background-color: lightgray;
      margin: 0 40rpx;
    }
  }
}
</style>
