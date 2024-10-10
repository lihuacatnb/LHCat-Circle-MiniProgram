<template>
  <view class="partner tn-safe-area-inset-bottom">
    <!-- 顶部自定义导航 -->
    <tn-nav-bar fixed alpha customBack>
      <view slot="back" class='tn-custom-nav-bar__back'
        @click="goBack">
        <text class='icon tn-icon-left'></text>
        <text class='icon tn-icon-home-capsule-fill'></text>
      </view>
    </tn-nav-bar>
    
    
    <view class="" :style="{paddingTop: vuex_custom_bar_height + 'px'}">
      
      <view class="tn-flex tn-flex-col-top tn-margin tn-cat-shadow tn-padding" v-for="(item,index) in 18" :key="index" @click="tn('/messagePages/chat')">
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
              <text class="tn-color-cat tn-text-lg tn-text-bold">抓住那只猪</text>
              <text class="tn-color-gray tn-padding-left-sm tn-padding-right-xs">市场经理</text>
            </view>
            <!-- <view class="justify-content-item tn-round tn-text-xs tn-bg-gray--light tn-color-cat" style="padding: 10rpx 20rpx;">
              详 情
            </view> -->
          </view>
          <view class=" tn-padding-top-xs">
            <text class="tn-color-gray">广州抓住那只猪科技有限公司</text>
          </view>
          <view class=" tn-padding-top-xs">
            <text class="tn-color-cat">专业承接UI、前端开发</text>
          </view>
          <view class="tn-flex tn-flex-row-between tn-flex-col-between tn-margin-top-sm">
            <view class="justify-content-item tn-round tn-text-xs tn-bg-orangered--light tn-color-orangered" style="padding: 5rpx 15rpx;">
              <text class="tn-padding-right-xs">￥</text> 2000元起 合作
            </view>
            <view class="justify-content-item tn-color-gray tn-text-center tn-color-gray">
              <text class="tn-icon-phone tn-padding-right-xs tn-text-df"></text>
              <text class="tn-text-sm">13699999999</text>
            </view>
          </view>
        </view>
      </view>
      
    </view>
  </view>
</template>

<script>
  import template_page_mixin from '@/libs/mixin/template_page_mixin.js'
  export default {
    name: 'TemplatePartner',
    mixins: [template_page_mixin],
    data(){
      return {}
    },
    methods: {
      
    }
  }
</script>

<style lang="scss" scoped>
  /* 胶囊*/
  .tn-custom-nav-bar__back {
    width: 100%;
    height: 100%;
    position: relative;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    box-sizing: border-box;
    background-color: rgba(0, 0, 0, 0.15);
    border-radius: 1000rpx;
    border: 1rpx solid rgba(255, 255, 255, 0.5);
    color: #FFFFFF;
    font-size: 18px;
    
    .icon {
      display: block;
      flex: 1;
      margin: auto;
      text-align: center;
    }
    
    &:before {
      content: " ";
      width: 1rpx;
      height: 110%;
      position: absolute;
      top: 22.5%;
      left: 0;
      right: 0;
      margin: auto;
      transform: scale(0.5);
      transform-origin: 0 0;
      pointer-events: none;
      box-sizing: border-box;
      opacity: 0.7;
      background-color: #FFFFFF;
    }
  }
  
  /* 页面阴影 start*/
  .tn-cat-shadow {
    border-radius: 15rpx;
    box-shadow: 0rpx 0rpx 50rpx 0rpx rgba(0, 0, 0, 0.07);
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
