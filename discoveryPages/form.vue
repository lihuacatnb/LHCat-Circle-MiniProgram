<template>
  <view class="template-integral tn-safe-area-inset-bottom">
    <!-- 顶部自定义导航 -->
    <tn-nav-bar fixed alpha customBack>
      <view slot="back" class='tn-custom-nav-bar__back'
        @click="goBack">
        <text class='icon tn-icon-left'></text>
        <text class='icon tn-icon-home-capsule-fill'></text>
      </view>
    </tn-nav-bar>
    
    
    <view class="" :style="{paddingTop: vuex_custom_bar_height + 'px'}" style="background: linear-gradient(180deg, #FEF5E4, #F9FFF9);">
      <view class="tn-padding-top-xl">
        <view class="tn-flex adver-wrap ">
           <view class="tn-text-center tn-flex-1">
             <view class="tn-text-xxl tn-text-bold">6,908</view>
             <view class="tn-text-lg  tn-padding-left-xs" style="">可提现</view>
           </view>
           <view class="tn-text-center tn-flex-1">
             <view class="tn-text-xxl tn-text-bold">1,005</view>
             <view class="tn-text-lg tn-padding-left-xs" style="">待入账</view>
           </view>
           <view class="tn-text-center tn-flex-1">
             <view class="tn-text-xxl tn-text-bold">80,980</view>
             <view class="tn-text-lg tn-padding-left-xs" style="">总收益</view>
           </view>
         </view>
         <view class="tn-padding-top-xl">
           <view class="tn-text-center tn-color-gray">
             已提现 73,067
           </view>
         </view>

      </view>
      </view>
    
    
    <view class="tn-margin">
      <view class="button-vip tn-flex tn-flex-row-between tn-flex-col-center tn-shadow-blur" style="background: linear-gradient(-120deg, #3E445A, #31374A, #2B3042, #262B3C);">
        
        <view class="tn-margin-left">
          <view class='title' style="color: #F1C68E;">
            <text class="tn-text-bold tn-text-xl">猪猪银行</text>
            <!-- <text class="tn-icon-vip-text tn-text-center" style="position: absolute;margin: -22rpx 0 0 0;font-size: 92rpx;"></text> -->
          </view>
          <view class='tn-color-white tn-padding-top-sm'>6122 **** **** 60606</view>
        </view>
        <view class="tn-margin-right">
          <tn-button shape="round" backgroundColor="#F1C68E" fontColor="#634738" padding="10rpx 0" width="160rpx" shadow>
            <!-- <text class="tn-icon-vip tn-padding-right-sm tn-text-lg"></text> -->
            <text class="tn-text-bold">换 卡</text>
          </tn-button>
        </view>
        
      </view>
    </view>
    

    <!-- 边距间隔 -->
    <view class="tn-strip-bottom"></view>
    
    <!-- 更多信息-->
    <view class="tn-padding-top-sm tn-padding-bottom-sm">
      <tn-list-cell :hover="true" :unlined="true" :radius="true" :fontSize="34">
        <view class="tn-flex tn-flex-col-center">
          <view class="tn-flex-1">费用</view>
          <view class="tn-margin-left-sm" style="font-size: 28rpx;">0.01元</view>
        </view>
      </tn-list-cell>
      <tn-list-cell :hover="true" :unlined="true" :radius="true" :fontSize="34">
        <view class="tn-flex tn-flex-col-center">
          <view class="tn-flex-1">活动人数</view>
          <view class="tn-margin-left-sm" style="font-size: 28rpx;">129人</view>
        </view>
      </tn-list-cell>
      <tn-list-cell :hover="true" :unlined="true" :radius="true" :fontSize="34">
        <view class="tn-flex tn-flex-col-center">
          <view class="tn-flex-1">活动时长</view>
          <view class="tn-margin-left-sm" style="font-size: 28rpx;">90天</view>
        </view>
      </tn-list-cell>
    </view>

    <!-- 边距间隔 -->
    <view class="tn-strip-bottom"></view>
    
    
    <view class="tn-flex tn-flex-row-between tn-strip-bottom-min tn-padding tn-margin-top-xs" v-for="(item, index) in setList" :key="index" @click="tn(item.url)">
      <view class="justify-content-item">
        <view class="tn-text-bold tn-text-lg">
          {{ item.title }}
        </view>
      </view>
      <view class="justify-content-item tn-text-lg tn-color-grey">
        <view class="tn-icon-right"></view>
      </view>
    </view>
    
    <!-- 边距间隔 -->
    <view class="tn-strip-bottom"></view>
    
    <!-- 悬浮按钮-->
    <view class="tn-flex tn-footerfixed">
      <view class="tn-flex-1 justify-content-item tn-margin-sm tn-text-center">
        <tn-button backgroundColor="#3668FC" padding="40rpx 0" width="60%" shadow fontBold @tap="upload">
          <!-- <text class="tn-icon-light tn-padding-right-xs tn-color-black"></text> -->
          <text class="tn-color-white">确认提现</text>
          <!-- <text class="tn-icon-camera tn-padding-left-xs tn-color-black"></text> -->
        </tn-button>
      </view>
    </view>
    
  </view>
</template>

<script>
  import template_page_mixin from '@/libs/mixin/template_page_mixin.js'
  export default {
    name: 'TemplateIntegral',
    mixins: [template_page_mixin],
    data(){
      return {
        setList: [
        	{
        		title: "版权所属",
        		url: "/minePages/content",
        	},
        	{
        		title: "使用协议",
        		url: "/minePages/content",
        	},
        	{
        		title: "隐私政策",
        		url: "/minePages/content",
        	},
          {
          	title: "帮助中心",
          	url: "/minePages/help",
          },
        	{
        		title: "版本更新",
        		url: "/minePages/version",
        	}
        ]
      }
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
  
  /* 顶部背景图 start */
  .top-backgroup {
    height: 450rpx;
    z-index: -1;
  
    .backgroud-image {
      width: 100%;
      height: 450rpx;
      // z-index: -1;
    }
  }
  /* 顶部背景图 end */
  
  /* 底部悬浮按钮 start*/
  .tn-tabbar-height {
  	min-height: 100rpx;
  	height: calc(120rpx + env(safe-area-inset-bottom) / 2);
  }
  .tn-footerfixed {
    position: fixed;
    width: 100%;
    bottom: calc(30rpx + env(safe-area-inset-bottom));
    z-index: 1024;
    box-shadow: 0 1rpx 6rpx rgba(0, 0, 0, 0);
    
  }
  /* 底部悬浮按钮 end*/
  
  /* 页面 start*/
  .integral-shadow{
    border-radius: 15rpx;
    box-shadow: 0rpx 0rpx 50rpx 0rpx rgba(0, 0, 0, 0.07);
  }
  
  /* 阴影 start*/
  .tn-shadow {
    border-radius: 15rpx;
    box-shadow: 0rpx 0rpx 50rpx 0rpx rgba(0, 0, 0, 0.07);
  }
  
  .integral-wrap {
    position: relative;
    z-index: 1;
  }
  /* 页面 end*/
  
  /* 翘边阴影*/
  .shadow-warp {
  	position: relative;
  	box-shadow: 0 10rpx 10rpx rgba(0, 0, 0, 0.01);
  }
  
  .shadow-warp:before,
  .shadow-warp:after {
  	position: absolute;
  	content: "";
  	top: 20rpx;
  	bottom: 30rpx;
  	left: 20rpx;
  	width: 50%;
  	box-shadow: 0 30rpx 20rpx rgba(0, 0, 0, 0.2);
  	transform: rotate(-3deg);
  	z-index: -1;
  }
  
  .shadow-warp:after {
  	right: 20rpx;
  	left: auto;
  	transform: rotate(3deg);
  }
  
  // 银行卡
  .button-vip {
    width: 100%;
    height: 150rpx;
    border-radius: 15rpx;
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
      background-image: url(https://resource.tuniaokj.com/images/cool_bg_image/icon_bg.png);
    }    
  }
  
  
  /* 间隔线 start*/
  .tn-strip-bottom-min {
    width: 100%;
    border-bottom: 1rpx solid #F8F9FB;
  }
  
  .tn-strip-bottom {
   width: 100%;
   border-bottom: 20rpx solid rgba(241, 241, 241, 0.8);
  }
   /* 间隔线 end*/
</style>
