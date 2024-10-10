<template>
	<view class="message tn-safe-area-inset-bottom">
    <!-- 顶部自定义导航 -->
    <tn-nav-bar :isBack="false" :bottomShadow="false" backgroundColor="none">
      <view class="custom-nav tn-flex tn-flex-col-center tn-flex-row-left" @click="tn('/minePages/message')">
        <view class="custom-nav__back">
          <view class="tn-icon-clear tn-color-cat" style="font-size: 50rpx;">
          </view>
        </view>
      </view>
    </tn-nav-bar>
    
    <view class="tn-margin-top-sm tn-padding-bottom-lg">
      
      
      <!-- 方式1 start-->
      <view class="tn-flex tn-message-fixed" :style="{paddingTop: vuex_custom_bar_height + 'px'}">
        <view class="tn-flex-1 tn-padding-sm tn-margin-xs tn-radius">
          <view class="tn-flex tn-flex-direction-column tn-flex-row-center tn-flex-col-center">
            <view class="icon1__item--icon tn-flex tn-flex-row-center tn-flex-col-center tn-shadow-blur" style="background-color: #F3F2F7;color: #7C8191;">
              <view class="tn-icon-reply">
              </view>
            </view>  
            <view class="tn-color-black tn-text-center">
              <text class="tn-text-ellipsis">互 动</text>
            </view>
          </view>
        </view>
        <view class="tn-flex-1 tn-padding-sm tn-margin-xs tn-radius">
          <view class="tn-flex tn-flex-direction-column tn-flex-row-center tn-flex-col-center">
            <view class="icon1__item--icon tn-flex tn-flex-row-center tn-flex-col-center tn-shadow-blur" style="background-color: #F3F2F7;color: #7C8191;">
              <view class="tn-icon-like">
                <tn-badge backgroundColor="#E72F8C" fontColor="#FFFFFF" :absolute="true" :fontSize="16">
                  <text>12</text>
                </tn-badge>
              </view>
            </view>  
            <view class="tn-color-black tn-text-center">
              <text class="tn-text-ellipsis">爱 心</text>
            </view>
          </view>
        </view>
        <view class="tn-flex-1 tn-padding-sm tn-margin-xs tn-radius">
          <view class="tn-flex tn-flex-direction-column tn-flex-row-center tn-flex-col-center">
            <view class="icon1__item--icon tn-flex tn-flex-row-center tn-flex-col-center tn-shadow-blur" style="background-color: #F3F2F7;color: #7C8191;">
              <view class="tn-icon-star">
              </view>
            </view>  
            <view class="tn-color-black tn-text-center">
              <text class="tn-text-ellipsis">花 束</text>
            </view>
          </view>
        </view>
        <view class="tn-flex-1 tn-padding-sm tn-margin-xs tn-radius">
          <view class="tn-flex tn-flex-direction-column tn-flex-row-center tn-flex-col-center">
            <view class="icon1__item--icon tn-flex tn-flex-row-center tn-flex-col-center tn-shadow-blur" style="background-color: #F3F2F7;color: #7C8191;">
              <view class="tn-icon-notice">
                <tn-badge backgroundColor="#E72F8C" fontColor="#FFFFFF" :absolute="true" :fontSize="16">
                  <text>99+</text>
                </tn-badge>
              </view>
            </view>  
            <view class="tn-color-black tn-text-center">
              <text class="tn-text-ellipsis">通 知</text>
            </view>
          </view>
        </view>
      </view>
      <!-- 方式1 end-->
      
      
      <view class="" :style="{paddingTop: vuex_custom_bar_height + 'px'}" >
        <view class="" style="padding-top: 200rpx;">
          <view class="tn-flex tn-flex-col-top tn-margin tn-cat-shadow tn-padding">
            <view class="">
              <view class="icon15__item--icon tn-flex tn-flex-row-center tn-flex-col-center tn-shadow-blur" style="background-color: #F3F2F7;color: #7C8191;">
                <view class="tn-icon-notice"></view>
              </view>
            </view>
            <view class="tn-padding-left-sm" style="width: 100%;">
              <view class="tn-flex tn-flex-row-between tn-flex-col-between">
                <view class="justify-content-item">
                  <text class="tn-color-cat tn-text-lg tn-text-bold">系统通知</text>
                </view>
                <view class="justify-content-item tag">
                  官 方
                </view>
              </view>
              <view class=" tn-padding-top-xs  tn-text-ellipsis-2">
                <text class="tn-color-gray">实名认证已通过</text>
              </view>
              <view class="tn-flex tn-flex-row-between tn-flex-col-between tn-margin-top-sm">
                <view class="justify-content-item tn-round tn-text-xs tn-bg-orangered--light tn-color-orangered" style="padding: 5rpx 15rpx;">
                  <text class="tn-padding-right-xs">#</text> 公 告
                </view>
                <view class="justify-content-item tn-color-gray tn-text-center tn-color-gray">
                  <text class="tn-icon-time tn-padding-right-xs tn-text-df"></text>
                  <text class="tn-text-sm">2024-10-7 20:15</text>
                </view>
              </view>
            </view>
          </view>
        </view>
      </view>
      
      <view class="tn-flex tn-flex-col-top tn-margin tn-cat-shadow tn-padding">
        <view class="">
          <view class="icon15__item--icon tn-flex tn-flex-row-center tn-flex-col-center tn-shadow-blur" style="background-color: #F3F2F7;color: #7C8191;">
            <view class="tn-icon-constellation"></view>
          </view>
        </view>
        <view class="tn-padding-left-sm" style="width: 100%;">
          <view class="tn-flex tn-flex-row-between tn-flex-col-between">
            <view class="justify-content-item">
              <text class="tn-color-cat tn-text-lg tn-text-bold">智能助手</text>
            </view>
            <view class="justify-content-item tag">
              官 方
            </view>
            
            
          </view>
          <view class=" tn-padding-top-xs  tn-text-ellipsis-2">
            <text class="tn-color-gray">您有多条消息未读</text>
          </view>
          <view class="tn-flex tn-flex-row-between tn-flex-col-between tn-margin-top-sm">
            <view class="justify-content-item tn-round tn-text-xs tn-bg-orangered--light tn-color-orangered" style="padding: 5rpx 15rpx;">
              <text class="tn-padding-right-xs">#</text> 10条未读消息
            </view>
            <view class="justify-content-item tn-color-gray tn-text-center tn-color-gray">
              <text class="tn-icon-time tn-padding-right-xs tn-text-df"></text>
              <text class="tn-text-sm">2024-10-7 20:45</text>
            </view>
          </view>
        </view>
      </view>
      
      <view class="tn-flex tn-flex-col-top tn-margin tn-cat-shadow tn-padding" v-for="(item,index) in 1" :key="index" @click="tn('/messagePages/chat')">
        <view class="">
          <view class="logo-pic tn-shadow">
            <view class="logo-image">
              <view class="tn-shadow-blur" style="background-image:url('https://resource.tuniaokj.com/images/blogger/blogger_beibei.jpg');width: 100rpx;height: 100rpx;background-size: cover;">
              </view>
            </view>
          </view>
        </view>
        <view class="tn-padding-left-sm" style="width: 100%;">
          <view class="tn-flex tn-flex-row-between tn-flex-col-between">
            <view class="justify-content-item">
              <text class="tn-color-cat tn-text-lg tn-text-bold">狸花花</text>
            </view>
            <!-- <view class="justify-content-item tn-round tn-text-xs tn-bg-gray--light tn-color-cat" style="padding: 10rpx 20rpx;">
              社 区
            </view> -->
          </view>
          <view class=" tn-padding-top-xs">
            <text class="tn-color-gray">人生就是这样，得意淡然，失意坦然；喜而不狂，忧而不伤。</text>
          </view>
          <view class="tn-flex tn-flex-row-between tn-flex-col-between tn-margin-top-sm">
            <view class="justify-content-item tn-round tn-text-xs tn-bg-orangered--light tn-color-orangered" style="padding: 5rpx 15rpx;">
              <text class="tn-padding-right-xs">#</text> 5条未读消息
            </view>
            <view class="justify-content-item tn-color-gray tn-text-center tn-color-gray">
              <text class="tn-icon-time tn-padding-right-xs tn-text-df"></text>
              <text class="tn-text-sm">2024-10-7 21:08</text>
            </view>
          </view>
        </view>
      </view>
      
    </view>
    
    <view class="tn-tabbar-height"></view>
    
	</view>
</template>

<script>
	export default {
    name: 'Message',
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
      // 跳转
      tn(e) {
        uni.navigateTo({
          url: e,
        });
      },
		}
	}
</script>

<style lang="scss" scoped>
	.message{
	  max-height: 100vh;
	}
  
  /* 自定义导航栏内容 start */
  .custom-nav {
    height: 100%;
    
    &__back {
      margin: auto 5rpx;
      font-size: 40rpx;
      margin-right: 10rpx;
      flex-basis: 5%;
      width: 100rpx;
      position: absolute;
    }
  }
  /* 自定义导航栏内容 end */
  
  /* 底部安全边距 start*/
  .tn-tabbar-height {
  	min-height: 120rpx;
  	height: calc(140rpx + env(safe-area-inset-bottom) / 2);
    height: calc(140rpx + constant(safe-area-inset-bottom));
  }
  
  .tn-message-fixed{
    position: fixed;
    background-color: rgba(255,255,255,1);
    box-shadow: 0rpx 0rpx 30rpx 0rpx rgba(0, 0, 0, 0.07);
    top: 0;
    width: 100%;
    transition: all 0.25s ease-out;
    z-index: 100;
  }
  
  
  
  /* 图标容器1 start */
  .icon1 {
    &__item {
      width: 30%;
      background-color: #FFFFFF;
      border-radius: 10rpx;
      padding: 30rpx;
      margin: 20rpx 10rpx;
      transform: scale(1);
      transition: transform 0.3s linear;
      transform-origin: center center;
      
      &--icon {
        width: 90rpx;
        height: 90rpx;
        font-size: 60rpx;
        border-radius: 50%;
        margin-bottom: 18rpx;
        position: relative;
        z-index: 1;
        
        &::after {
          content: " ";
          position: absolute;
          z-index: -1;
          width: 100%;
          height: 100%;
          left: 0;
          bottom: 0;
          border-radius: inherit;
          opacity: 1;
          transform: scale(1, 1);
          background-size: 100% 100%;
          background-image: url(https://resource.tuniaokj.com/images/cool_bg_image/icon_bg5.png);
        }
      }
    }
  }
  
  .tn-color-cat{
    color: #1D2541;
  }
  
  /* 页面阴影 start*/
  .tn-cat-shadow {
    border-radius: 15rpx;
    box-shadow: 0rpx 0rpx 50rpx 0rpx rgba(0, 0, 0, 0.07);
  }
  
  
  /* 标签*/
  .tag{
    margin: 10rpx 0 10rpx 10rpx;
    color: #7C8191;
    background-color: #F3F2F7;
    padding: 4rpx 14rpx 6rpx;
    border-radius: 10rpx;
    font-size: 20rpx;
  }
  
  /* 图标容器15 start */
  .icon15 {
    &__item {
      width: 30%;
      background-color: #FFFFFF;
      border-radius: 10rpx;
      padding: 30rpx;
      margin: 20rpx 10rpx;
      transform: scale(1);
      transition: transform 0.3s linear;
      transform-origin: center center;
      
      &--icon {
        width: 105rpx;
        height: 105rpx;
        font-size: 60rpx;
        border-radius: 50%;
        margin-bottom: 18rpx;
        position: relative;
        z-index: 1;
        
        &::after {
          content: " ";
          position: absolute;
          z-index: -1;
          width: 100%;
          height: 100%;
          left: 0;
          bottom: 0;
          border-radius: inherit;
          opacity: 1;
          transform: scale(1, 1);
          background-size: 100% 100%;
  
            
        }
      }
    }
  }
  
  /* 用户头像 start */
  .logo-image {
    width: 100rpx;
    height: 100rpx;
    position: relative;
  }
  
  .logo-pic {
    background-size: cover;
    background-repeat: no-repeat;
    // background-attachment:fixed;
    background-position: top;
    border: 1rpx solid rgba(255,255,255,0.05);
    box-shadow: 0rpx 0rpx 80rpx 0rpx rgba(0, 0, 0, 0.15);
    border-radius: 50%;
    overflow: hidden;
    // background-color: #FFFFFF;
  }
  
</style>
