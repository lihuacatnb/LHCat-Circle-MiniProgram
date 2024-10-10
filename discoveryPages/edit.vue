<template>
	<view class="template-edit tn-safe-area-inset-bottom">
    <!-- 顶部自定义导航 -->
    <tn-nav-bar fixed alpha customBack>
      <view slot="back" class='tn-custom-nav-bar__back'
        @click="goBack">
        <text class='icon tn-icon-left'></text>
        <text class='icon tn-icon-home-capsule-fill'></text>
      </view>
    </tn-nav-bar>
		
    <view class="tn-safe-area-inset-bottom" :style="{paddingTop: vuex_custom_bar_height + 'px'}">
      
      <view class="tn-flex tn-flex-row-between tn-flex-col-center tn-padding-top tn-margin">
        <view class="tn-flex justify-content-item">
          <view class="tn-bg-black tn-color-white tn-text-center" style="border-radius: 100rpx;margin-right: 8rpx;width: 45rpx;height: 45rpx;line-height: 45rpx;">
            <text class="tn-icon-topics" style="font-size: 30rpx;"></text>
          </view>
          <view class="tn-text-lg tn-padding-right-xs tn-text-bold">
            描述一下想反馈的问题
            <text class="tn-color-purplered tn-padding-left-xs">*</text>
          </view>
        </view>
        <view class="justify-content-item tn-text-df tn-color-grey">
          <text class="tn-padding-xs">500字内</text>
          <text class="tn-icon-keyboard-circle"></text>
        </view>
      </view>
      
      <!-- <view class="tn-margin tn-bg-gray--light" style="border-radius: 10rpx;padding: 20rpx 30rpx;">
      	<input placeholder="写下一句简短的标题" name="input" placeholder-style="color:#AAAAAA" ></input>
      </view> -->
      <view class="tn-margin tn-bg-gray--light tn-padding" style="border-radius: 10rpx;">
        <textarea maxlength="500" placeholder="来吧,请尽情批判我!"
          placeholder-style="color:#AAAAAA"></textarea>
      </view>
      
      <view class="tn-flex tn-flex-row-between tn-flex-col-center tn-padding-top-xl tn-margin">
        <view class="tn-flex justify-content-item">
          <view class="tn-bg-black tn-color-white tn-text-center" style="border-radius: 100rpx;margin-right: 8rpx;width: 45rpx;height: 45rpx;line-height: 45rpx;">
            <text class="tn-icon-image" style="font-size: 30rpx;"></text>
          </view>
          <view class="tn-text-lg tn-padding-right-xs tn-text-bold">
            上传一下具体的问题图片
            <text class="tn-color-purplered tn-padding-left-xs">*</text>
          </view>
        </view>
        <view class="justify-content-item tn-text-df tn-color-grey" @tap="clear">
          <text class="tn-padding-xs">清空上传</text>
          <text class="tn-icon-delete"></text>
        </view>
      </view>
      
      
      
      
      <view class="tn-margin-left tn-padding-top-xs">
        <tn-image-upload-drag
          ref="imageUpload"
          :action="action"
          :width="236"
          :height="236"
          :formData="formData"
          :fileList="fileList"
          :disabled="disabled"
          :autoUpload="autoUpload"
          :maxCount="maxCount"
          :showUploadList="showUploadList"
          :showProgress="showProgress"
          :deleteable="deleteable"
          :customBtn="customBtn"
          @sort-list="onSortList"
        />

      </view>
      <!-- 悬浮按钮-->
      <view class="tn-flex tn-footerfixed">
        
        <view class="tn-flex-3 justify-content-item tn-margin-sm tn-text-center">
          <view class="tn-padding-xl" shadow @click="showModal">
            <text class="tn-icon-tip-fill tn-color-purplered tn-padding-right-xs"></text> 
            <text class="tn-color-gray">这些禁止上传</text>
          </view>
          <tn-button backgroundColor="#3668FC" padding="40rpx 0" width="60%" shadow fontBold @tap="upload">
            <!-- <text class="tn-icon-camera tn-padding-right-xs tn-color-white"></text> -->
            <text class="tn-color-white">发送反馈</text>
            <!-- <text class="tn-icon-camera tn-padding-left-xs tn-color-white"></text> -->
          </tn-button>
        </view>
      </view>
      
    </view>
    
    <tn-modal v-model="show1" :custom="true" :showCloseBtn="true">
      <view class="custom-modal-content">
        <view class="">
          <view class="tn-text-lg tn-text-bold tn-color-purplered tn-text-center tn-padding">温馨提示 · 此类禁止</view>
          <view class="tn-text-center tn-color-gray" style="padding: 20rpx 20rpx;">
            <view class="">& 黄赌毒</view>
            <view class="">& 其他一大堆描述</view> 
             <view class="">& 其他一大堆描述</view>
             <view class="">& 其他一大堆描述</view>
             <view class="">& 其他一大堆描述</view>
             <view class="">& 其他一大堆描述</view>
          </view>  
        </view>
        <view class="tn-flex-1 justify-content-item tn-margin-sm tn-text-center">
          <tn-button backgroundColor="#3668FC" padding="40rpx 0" width="60%" shadow fontBold >
            <text class="tn-color-white">我知道了</text>
          </tn-button>
        </view>
      </view>
    </tn-modal>
    
    <view class='tn-tabbar-height'></view>
    
	</view>
</template>

<script>
  import template_page_mixin from '@/libs/mixin/template_page_mixin.js'
	export default {
    name: 'TemplateEdit',
    mixins: [template_page_mixin],
		data() {
			return {
				action: 'https://www.hualigs.cn/api/upload',
				// action: '',
				formData: {
				  apiType: 'this,ali',
				  token: 'dffc1e06e636cff0fdf7d877b6ae6a2e',
				  image: null
				},
				fileList: [{url: 'https://cdn.nlark.com/yuque/0/2022/jpeg/280373/1663571007436-assets/web-upload/e3fdeb91-d8d1-4187-8d91-593559543af3.jpeg'}, {url: 'https://cdn.nlark.com/yuque/0/2022/jpeg/280373/1663228733212-assets/web-upload/d390672d-01d0-43a7-bf25-5d607be910e7.jpeg'}],
				showUploadList: true,
				customBtn: false,
				autoUpload: true,
				showProgress: false,
				deleteable: true,
				customStyle: false,
				maxCount: 5,
				disabled: false,
        
        show1: false,
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
      // 手动上传文件
      upload() {
        this.$refs.imageUpload.upload()
      },
      // 手动清空列表
      clear() {
        this.$refs.imageUpload.clear()
      },
      // 图片拖拽重新排序
      onSortList(list) {
        console.log(list);
      },
      
      // 弹出模态框
      showModal(event) {
        this.openModal()
      },
      // 打开模态框
      openModal() {
        this.show1 = true
      },
		}
	}
</script>

<style lang="scss" scoped>
	.template-edit{
	}
  
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

</style>
