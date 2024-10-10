<template>
  <view class="discovery tn-safe-area-inset-bottom">
    <swiper class="card-swiper" @click="tn('')" :circular="true"
      :autoplay="false" duration="500" interval="8000" @change="cardSwiper"> 
      <swiper-item v-for="(item,index) in swiperList" :key="index" :class="cardCur==index?'cur':''">
        <view class="swiper-item image-banner">
          <image :src="item.url" mode="aspectFill" v-if="item.type=='image'"></image>
        </view>
        
        <view class="swiper-item-text">
          <view class="tn-padding swiper-item-title">
            <view class="tn-text-bold tn-color-white" style="font-size: 40rpx;">{{item.title}}</view>
            <view class="tn-color-white tn-padding-top" style="font-size: 25rpx;">{{item.name}}</view>
          </view>
        </view>
      </swiper-item>
    </swiper>
    <view class="indication">
        <block v-for="(item,index) in swiperList" :key="index">
            <view class="spot" :class="cardCur==index?'active':''"></view>
        </block>
    </view>
    
    
    <view class="tn-margin-top-sm">
      <tn-sticky :offsetTop="0" :customNavHeight="vuex_custom_bar_height">
        <tn-tabs :list="fixedList" :current="current" :isScroll="true" activeColor="#000" :bold="true" :fontSize="32" :badgeOffset="[20, 50]" @change="tabChange" backgroundColor="#FFFFFF99" :height="110"></tn-tabs>
      </tn-sticky>
    </view>
    
    
    <view class="" v-if="current==0">
      <view class="" style="padding: 30rpx 20rpx;" >
        <tn-waterfall ref="waterfall" v-model="list" @finish="handleWaterFallFinish">
          <template v-slot:left="{ leftList }">
            <view v-for="(item, index) in leftList" :key="item.id" class="product__item" @click="tn('')">
              <view class="item__image">
                <tn-lazy-load :threshold="-450" height="100%" :image="item.mainImage" :index="item.id" imgMode="widthFix"></tn-lazy-load>
              </view>
              <view class="item__data">
                <view class="item__title-container">
					<text class="item__title tn-color-cat">{{ item.title }}</text>
                </view>
                <view v-if="item.tags && item.tags.length > 0" class="item__tags-container">
                  <view v-for="(tagItem, tagIndex) in item.tags" :key="tagIndex" class="item__tag">{{ tagItem }}</view>
                </view>
    
                <view class="tn-flex tn-flex-row-between tn-flex-col-center tn-padding-top-xs">
                  <view class="justify-content-item">
                    <view class="tn-flex tn-flex-col-center tn-flex-row-left">
                      <view class="logo-pic">
                        <view class="logo-image">
                          <view class="" :style="'background-image:url('+ item.userImage +');width: 40rpx;height: 40rpx;background-size: cover;'">
                          </view>
                        </view>
                      </view>
                      <view class="tn-padding-left-xs">
                        <text class="tn-color-gray tn-text-sm">{{ item.userName }}</text>
                      </view>
                
                    </view>
                  </view>
                  <view class="justify-content-item">
                    <text class="tn-icon-rocket tn-color-gray tn-padding-right-xs"></text>
                    <text class="tn-color-gray">{{ item.viewUser.viewUserCount }}</text>
                  </view>
                </view>
                
                
              </view>
            </view>
          </template>
         <template v-slot:right="{ rightList }">
            <view v-for="(item, index) in rightList" :key="item.id" class="product__item" @click="tn('')">
              <view class="item__image">
                <tn-lazy-load :threshold="-450" height="100%" :image="item.mainImage" :index="item.id" imgMode="widthFix"></tn-lazy-load>
              </view>
              <view class="item__data">
                <view class="item__title-container">
                  <text class="item__title tn-color-cat">{{ item.title }}</text>
                </view>
                <view class="item__tags-container">
                  <view v-for="(tagItem, tagIndex) in item.tags" :key="tagIndex" class="item__tag">{{ tagItem }}</view>
                </view>
                <view class="tn-flex tn-flex-row-between tn-flex-col-center tn-padding-top-xs">
                  <view class="justify-content-item">
                    <view class="tn-flex tn-flex-col-center tn-flex-row-left">
                      <view class="logo-pic">
                        <view class="logo-image">
                          <view class="" :style="'background-image:url('+ item.userImage +');width: 40rpx;height: 40rpx;background-size: cover;'">
                          </view>
                        </view>
                      </view>
                      <view class="tn-padding-left-xs">
                        <text class="tn-color-gray tn-text-sm">{{ item.userName }}</text>
                      </view>
                
                    </view>
                  </view>
                  <view class="justify-content-item">
                    <text class="tn-icon-rocket tn-color-gray tn-padding-right-xs"></text>
                    <text class="tn-color-gray">{{ item.viewUser.viewUserCount }}</text>
                  </view>
                </view>
              </view>
            </view>
          </template>
        </tn-waterfall>
      </view>
      <tn-load-more :status="loadStatus"></tn-load-more>
    </view>
    
    <view class="" v-if="current==1">
      <view class="" style="padding: 30rpx 20rpx;">
        <view class="tn-text-center" style="font-size: 200rpx;padding-top: 30rpx;">
          <text class="tn-icon-wea-wind tn-color-gray--light"></text>
        </view>
        <view class="tn-color-gray--disabled tn-text-center tn-text-lg">内容被台风吹走了1</view>
      </view>
    </view>
    <view class="" v-if="current==2">
      <view class="" style="padding: 30rpx 20rpx;">
        <view class="tn-text-center" style="font-size: 200rpx;padding-top: 30rpx;">
          <text class="tn-icon-wea-wind tn-color-gray--light"></text>
        </view>
        <view class="tn-color-gray--disabled tn-text-center tn-text-lg">内容被台风吹走了2</view>
      </view>
    </view>
  </view>
</template>

<script>
  import template_page_mixin from '@/libs/mixin/template_page_mixin.js'
  export default {
    name: 'Discovery',
    mixins: [template_page_mixin],
    data(){
      return {
        cardCur: 0,
        swiperList: [{
          id: 0,
          type: 'image',
          title: '休息，是为了走更长远的路',
          name: '记住，休息不是逃避，而是为了更好地出发',
          url: 'https://resource.tuniaokj.com/images/simple/banner3.jpg',
        }, {
          id: 1,
          type: 'image',
          title: '给自己一个深呼吸的机会',
          name: '闭上眼睛，让心灵在宁静中得到片刻的安宁',
          url: 'https://resource.tuniaokj.com/images/simple/banner1.jpg',
        }, {
          id: 2,
          type: 'image',
          title: '享受生活中的小确幸',
          name: '一杯咖啡，一本书，一个悠闲的下午',
          url: 'https://resource.tuniaokj.com/images/simple/banner2.jpg',
        }],
        /* tabs*/
        current: 0,
        fixedList: [
          {name: '推荐'},
          {name: '附近'},
          {name: '最新'},
        ],
        
        /* 瀑布流*/
        loadStatus: 'loadmore',
        list: [],
        data: [
          {
            title: '北京地区帮忙喂猫',
            userName: '北北',
            mainImage: 'https://resource.tuniaokj.com/images/simple/image0.jpg',
            userImage: 'https://resource.tuniaokj.com/images/blogger/avatar_1.jpeg',
            storeType: 1, // 1 自营 2 第三方店铺
            newProduct: true, // 是否为新品
            tags: ['北京','兼职'],
            viewUser: {
              latestUserAvatar: [
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_1.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_2.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_3.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_4.jpeg'},
              ],
              viewUserCount: 338
            },
          },
          {
            title: '小程序兼职开发',
            userName: '王不老',
            mainImage: 'https://resource.tuniaokj.com/images/simple/image1.jpg',
            userImage: 'https://resource.tuniaokj.com/images/blogger/avatar_2.jpeg',
            storeType: 1, // 1 自营 2 第三方店铺
            newProduct: false, // 是否为新品
            tags: ['兼职'],
            viewUser: {
              latestUserAvatar: [
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_1.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_2.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_3.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_4.jpeg'},
              ],
              viewUserCount: 289
            },
          },
          {
            title: '狸猫科技招人啦！！！',
            userName: '小花狸',
            mainImage: 'https://resource.tuniaokj.com/images/simple/image2.jpg',
            userImage: 'https://resource.tuniaokj.com/images/blogger/avatar_3.jpeg',
            storeType: 1, // 1 自营 2 第三方店铺
            newProduct: true, // 是否为新品
            tags: [],
            viewUser: {
              latestUserAvatar: [
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_1.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_2.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_3.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_4.jpeg'},
              ],
              viewUserCount: 381
            },
          },
          {
            title: '假期期间，来个保护抓娃娃机的',
            userName: '潮流玩家',
            mainImage: 'https://resource.tuniaokj.com/images/simple/image3.jpg',
            userImage: 'https://resource.tuniaokj.com/images/blogger/avatar_4.jpeg',
            storeType: 1, // 1 自营 2 第三方店铺
            newProduct: true, // 是否为新品
            tags: [],
            viewUser: {
              latestUserAvatar: [
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_1.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_2.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_3.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_4.jpeg'},
              ],
              viewUserCount: 526
            },
          },
          {
            title: '周日有组团一块出来飞盘的嘛？',
            userName: '胡桃',
            mainImage: 'https://resource.tuniaokj.com/images/simple/image4.jpg',
            userImage: 'https://resource.tuniaokj.com/images/blogger/avatar_1.jpeg',
            storeType: 1, // 1 自营 2 第三方店铺
            newProduct: false, // 是否为新品
            tags: [],
            viewUser: {
              latestUserAvatar: [
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_1.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_2.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_3.jpeg'},
                {src: 'https://resource.tuniaokj.com/images/blogger/avatar_4.jpeg'},
              ],
              viewUserCount: 372
            },
          }
        ]
      }
    },
    /* 瀑布流*/
    created() {
      this.getRandomData()
    },
    onReachBottom() {
      
    },
    methods: {
      // cardSwiper
      cardSwiper(e) {
        this.cardCur = e.detail.current
      },
      
      // 跳转
      tn(e) {
      	uni.navigateTo({
      		url: e,
      	});
      },
      // tab选项卡切换
      tabChange(index) {
        this.current = index
      },
      /* 瀑布流*/
      // 获取随机数据
      getRandomData() {
        this.loadStatus = 'loading'
        for (let i = 0; i < 10; i++) {
          let index = this.$t.number.randomInt(0, this.data.length - 1)
          let item = JSON.parse(JSON.stringify(this.data[index]))
          let price = this.getPrice(item.price)
          item.id = this.$t.uuid()
          item.priceInteger = price[0]
          item.priceDecimal = price[1]
          this.list.push(item)
        }
      },
      // 瀑布流加载完毕事件
      handleWaterFallFinish() {
        this.loadStatus = 'loadmore'
      },
      // 获取价格整数和小数部分
      getPrice(price) {
        const priceStr = String(price)
        if (priceStr.indexOf('.') !== -1) {
          return priceStr.split('.')
        } else {
          return [priceStr, '00']
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .discovery{
    max-height: 100vh;
  }
  /* 底部安全边距 start*/
  .tn-tabbar-height {
  	min-height: 120rpx;
  	height: calc(140rpx + env(safe-area-inset-bottom) / 2);
    height: calc(140rpx + constant(safe-area-inset-bottom));
  }
  
  /* 自定义导航栏内容 start */
  .custom-nav {
    height: 100%;
    
    &__back {
      margin-left: 30rpx;
      margin-top: 5rpx;
      font-size: 40rpx;
      flex-basis: 5%;
      width: 100rpx;
      position: absolute;
    }
  }
  /* 自定义导航栏内容 end */
  
  /* 轮播视觉差 start */
  .card-swiper {
    height: 680rpx !important;
  }
    
  .card-swiper swiper-item {
    width: 750rpx !important;
    left: 0rpx;
    box-sizing: border-box;
    // padding: 0rpx 30rpx 90rpx 30rpx;
    overflow: initial;
  }
    
  .card-swiper swiper-item .swiper-item {
    width: 100%;
    display: block;
    height: 100%;
    transform: scale(1);
    transition: all 0.2s ease-in 0s;
    overflow: hidden;
  }
    
  .card-swiper swiper-item.cur .swiper-item {
    transform: none;
    transition: all 0.2s ease-in 0s;
  }
    
  .card-swiper swiper-item .swiper-item-text {
    // background-color: rgba(0, 0, 0, 0.7);
    background-image: linear-gradient(0deg, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.05));
    margin-top: -260rpx;
    width: 100%;
    display: block;
    height: 50%;
    // border-radius: 10rpx;
    transform: translate(0rpx, 0rpx) scale(1);
    transition: all 0.6s ease 0s;
    overflow: hidden;
  }
    
  .card-swiper swiper-item.cur .swiper-item-text {
    // background-color: rgba(0, 0, 0, 0.7);
    background-image: linear-gradient(0deg, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.04));
    margin-top: -260rpx;
    width: 100%;
    transform: translate(0rpx, 0rpx) scale(1);
    transition: all 0.6s ease 0s;
  }
  
  
  .card-swiper swiper-item .swiper-item-title {
    transform: translate(50rpx, 0rpx) scale(0.9);
    transition: all 0.6s ease 0s;
    overflow: hidden;
  }
    
  .card-swiper swiper-item.cur .swiper-item-title {
    transform: translate(0rpx, 0rpx) scale(1);
    transition: all 0.6s ease 0s;
  }
  
  .image-banner{
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .image-banner image{
    width: 100%;
    height: 100%;
  }
  
  /* 轮播指示点 start*/
  .indication{
    z-index: 9999;
    width: 100%;
    height: 36rpx;
    position: absolute;
    display:flex;
    flex-direction:row;
    align-items:center;
    justify-content:center;
  }
  
  .spot{
    background-color: #FFFFFF;
    opacity: 0.6;
    width: 10rpx;
    height: 10rpx;
    border-radius: 20rpx;
    top: -60rpx;
    margin: 0 8rpx !important;
    position: relative;
  }
  
  .spot.active{
    opacity: 1;
    width: 30rpx;
    background-color: #FFFFFF;
  }
  
  /* 用户头像 start */
  .logo-image {
    width: 40rpx;
    height: 40rpx;
    position: relative;
  }
  
  .logo-pic {
    background-size: cover;
    background-repeat: no-repeat;
    // background-attachment:fixed;
    background-position: top;
    border: 1rpx solid rgba(255,255,255,0.05);
    // box-shadow: 0rpx 0rpx 80rpx 0rpx rgba(0, 0, 0, 0.15);
    border-radius: 50%;
    overflow: hidden;
    // background-color: #FFFFFF;
  }
  
  /* 瀑布流*/
  .product__item {
    background-color: #FFFFFF;
    overflow: hidden;
    margin: 0 10rpx;
    margin-bottom: 40rpx;
    // box-shadow: 0rpx 0rpx 30rpx 0rpx rgba(0, 0, 0, 0.07);
    
    .item {
      /* 图片 start */
      &__image {
        width: 100%;
        height: auto;
        background-color: #FFFFFF;
        border: 1rpx solid #F8F7F8;
        border-radius: 10rpx;
        overflow: hidden;
      }
      /* 图片 end */
      
      /* 内容 start */
      &__data {
        padding: 14rpx 0rpx;
      }
      
      /* 标题 start */
      &__title-container {
        text-align: justify;
        line-height: 38rpx;
        vertical-align: middle;
      }
      &__store-type {
        height: 28rpx;
        font-size: 20rpx;
        position: relative;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        padding: 4rpx;
        border-radius: 6rpx;
        white-space: nowrap;
        text-align: center;
        top: -2rpx;
        margin-right: 6rpx;
      }
      &__title {
        font-size: 30rpx;
      }
      /* 标题 end */
      
      /* 标签 start */
      &__tags-container {
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
        align-items: center;
        justify-content: flex-start;
      }
      &__tag {
        margin: 10rpx;
        color: #7C8191;
        background-color: #F3F2F7;
        padding: 4rpx 14rpx 6rpx;
        border-radius: 10rpx;
        font-size: 20rpx;
        
        &:first-child {
          margin-left: 0rpx !important;
        }
      }
      /* 标签 end */
      
      /* 价格 start */
      &__price-container {
        font-size: 24rpx;
        color: #E83A30;
        font-weight: bold;
      }
      &__price {
        &--unit {
          
        }
        &--integer {
          font-size: 38rpx;
        }
        &--decimal {
          
        }
      }
      /* 价格 end */
      /* 内容 end */
    }
  }
  
</style>
