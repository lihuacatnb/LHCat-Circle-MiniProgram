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
    
    
    <view class="integral-wrap" :style="{paddingTop: vuex_custom_bar_height + 'px'}" style="background: linear-gradient(180deg, #FEF5E4, #F9FFF9);">
      <view class="adver-wrap tn-shadow tn-margin tn-bg-white">
         <view class="tn-text-center" style="color: #E72F8C;padding: 30rpx 0;">
           <text style="font-size: 110rpx;margin-left: 20rpx;">129</text>
           <text class="tn-text-lg tn-text-bold tn-padding-left-xs" style="">积分</text>
         </view>
         <view class="tn-text-center tn-color-gray">
           积分可直接抵扣优惠
         </view>
         <view class="tn-flex-1 justify-content-item tn-margin-xs tn-text-center tn-padding-top tn-padding-bottom-xl">
           <tn-button shape="round" :plain="true" backgroundColor="#EF481F" padding="40rpx 0" width="50%" shadow :fontSize="32">
             <text class="" style="color: #EF481F;">每日签到</text>
           </tn-button>
         </view>  
       </view>

    </view>
    
    <view class="tn-margin-top-lg tn-margin-bottom">
      <view class="tn-flex tn-flex-row-between tn-strip-bottom-min tn-padding" v-for="(item,index) in integral" :key="index" >
        <view class="justify-content-item">
          <view class="tn-color-gray--dark tn-text-lg">
           {{item.name}}
          </view>
          <view class="tn-color-gray tn-padding-top-xs">
            {{item.time}}
          </view>
        </view>
        <view class="justify-content-item tn-text-xl tn-padding-top">
          <view :class="'tn-color-' + item.color + ';'"> {{item.integral}} </view>
        </view>
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
        
        integral: [{
          name: '每日签到',
          time: '2022-05-20 22:45:29',
          color: 'blue--dark',
          integral: '+10'
        },{
          name: '周边兑换 手机壳',
          time: '2022-05-18 20:20:50',
          color: 'purplered',
          integral: '-666'
        }, {
          name: '每日签到 连续签到7天',
          time: '2022-05-18 18:11:19',
          color: 'blue--dark',
          integral: '+100'
        }, {
          name: '每日签到 连续签到6天',
          time: '2022-05-17 13:42:42',
          color: 'blue--dark',
          integral: '+100'
        }, {
          name: '每日签到 连续签到5天',
          time: '2022-05-16 12:14:43',
          color: 'blue--dark',
          integral: '+50'
        }, {
          name: '每日签到 连续签到4天',
          time: '2022-05-15 10:21:08',
          color: 'blue--dark',
          integral: '+50'
        }, {
          name: '每日签到 连续签到3天',
          time: '2022-05-14 08:56:32',
          color: 'blue--dark',
          integral: '+50'
        }, {
          name: '每日签到',
          time: '2022-05-13 08:40:57',
          color: 'blue--dark',
          integral: '+10'
        }, {
          name: '每日签到',
          time: '2022-05-12 08:22:21',
          color: 'blue--dark',
          integral: '+10'
        }, {
          name: '每日签到',
          time: '2022-05-06 22:06:36',
          color: 'blue--dark',
          integral: '+10'
        }],
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
