<template>
  <view class="user">
    <view class="user-bg-1"></view>
    <view class="user-bg-2"></view>
    <view class="user-avatar">
      <UserAvatar></UserAvatar>
    </view>
    <view class="user-name"> 张三 </view>
    <view class="user-btn">
      <u-modal
        v-model="showLogoutConfirmPopup"
        title="退出登录"
        content="是否退出当前账号？"
        show-cancel-button
        @confirm="handleConfirmLogout"
        hover-class="none"
        :title-style="{ fontWeight: '700' }"
      ></u-modal>
      <u-button @click="handleLogout" plain="true">
        <u-icon name="icon-logout" custom-prefix="yun-iconfont"></u-icon>
        <text>退出登录</text>
      </u-button>
    </view>
  </view>
</template>
<script lang="ts" setup>
import { ref } from 'vue'
import UserAvatar from './components/UserAvatar/index.vue'

const showLogoutConfirmPopup = ref(false)

const handleLogout = () => {
  showLogoutConfirmPopup.value = true
}

const handleConfirmLogout = () => {
  console.log('logout')
}
</script>
<style lang="scss" scoped>
.user {
  display: flex;
  flex-direction: column;
  &-avatar {
    height: 128rpx;
    width: 128rpx;
    margin: 84rpx auto 20rpx auto;
    :deep(.u-avatar) {
      width: 100% !important;
      height: 100% !important;
    }
  }
  &-name {
    text-align: center;
    color: #262626;
    font-weight: 500;
    font-size: 40rpx;
    line-height: 56rpx;
    margin-bottom: 40rpx;
  }
  &-medal {
    .medal-details {
      margin: 0 32rpx;
      background: rgba(255, 255, 255, 0.5);
      border: 3rpx solid #ffffff;
      box-shadow: 0rpx 2rpx 16rpx rgba(32, 164, 206, 0.15);
      border-radius: 16rpx;
      padding-bottom: 24rpx;
      .details-img {
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 20rpx auto 0 auto;
        width: 256rpx;
        height: 256rpx;
        padding: 12rpx;
        image {
          width: 100%;
          height: 100%;
        }
        &::after {
          content: '';
          position: absolute;
          width: 5.35rpx;
          height: 200rpx;
          background: #ffffff;
          opacity: 0;
          transform: rotate(15deg) translateX(0);
          left: 0;
          top: 0;
        }

        &.is-active::after {
          animation: highLight 2s ease 0.5s;
        }
      }
      .details-info {
        margin-top: 24rpx;
        display: flex;
        text-align: center;
        justify-content: center;
        .info-1 {
          p {
            color: #8a8a8a;
            font-weight: 400;
            font-size: 24rpx;
            line-height: 40rpx;
            margin-bottom: 8rpx;
          }
          span {
            color: #585858;
            font-size: 26rpx;
            line-height: 42rpx;
          }
        }
        .info-2 {
          margin-right: 220rpx;
        }
      }
    }
  }
  &-btn {
    position: absolute;
    left: calc(50% - 112rpx);
    bottom: 160rpx;
    margin: 0 auto;
    text-align: center;
    width: 224rpx;
    height: 64rpx;
    :deep(.u-btn) {
      outline: none;
      color: transparent !important;
      background-color: #fdeced !important;
      text {
        color: #e8424a;
      }
    }
    u-icon {
      margin-right: 5rpx;
      color: #e8424a;
    }
  }
  &-bg-1,
  &-bg-2 {
    width: 256rpx;
    height: 256rpx;
    opacity: 0.5;
    filter: blur(200rpx);
    position: absolute;
  }
  &-bg-1 {
    left: 56rpx;
    top: 198rpx;
    background: #1581f3;
    transform: rotate(360deg);
  }
  &-bg-2 {
    left: 450rpx;
    top: 480rpx;
    background: #8142e8;
  }

  @keyframes highLight {
    0% {
      transform: rotate(15deg) translateX(0);
      opacity: 0.2;
    }
    99% {
      transform: rotate(15deg) translateX(250rpx);
    }
    100% {
      opacity: 0;
    }
  }
}
</style>
