<template>
  <div :style="{height: windowHeight, overflow: 'hidden'}">
    <!-- 自定义组件 -->
    <search @search="disableScroll" />
    <!-- 焦点图 -->
    <swiper class="banner" indicator-dots indicator-color="rgba(255, 255, 255, .6)" indicator-active-color="#fff" autoplay circular interval="3000">
      <swiper-item>
        <a href="">
          <img src="/static/uploads/banner1.png" alt="">
        </a>
      </swiper-item>
      <swiper-item>
        <a href="">
          <img src="/static/uploads/banner2.png" alt="">
        </a>
      </swiper-item>
      <swiper-item>
        <a href="">
          <img src="/static/uploads/banner3.png" alt="">
        </a>
      </swiper-item>
    </swiper>

    <!-- 主导航 -->
    <div class="navs">
      <a href="">
        <img src="/static/uploads/icon_index_nav_4@2x.png" alt="">
      </a>
      <a href="">
        <img src="/static/uploads/icon_index_nav_3@2x.png" alt="">
      </a>
      <a href="">
        <img src="/static/uploads/icon_index_nav_2@2x.png" alt="">
      </a>
      <a href="">
        <img src="/static/uploads/icon_index_nav_1@2x.png" alt="">
      </a>
    </div>

    <!-- 楼层 -->
    <div class="floors">
      <div class="floor">
        <!-- 标题 -->
        <div class="title">
          <img src="/static/uploads/pic_floor01_title.png" alt="">
        </div>
        <!-- 分类 -->
        <div class="items">
          <a href="">
            <img src="/static/uploads/pic_floor01_1@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor01_2@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor01_3@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor01_4@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor01_5@2x.png" alt="">
          </a>
        </div>
      </div>
      <div class="floor">
        <!-- 标题 -->
        <div class="title">
          <img src="/static/uploads/pic_floor02_title.png" alt="">
        </div>
        <!-- 分类 -->
        <div class="items">
          <a href="">
            <img src="/static/uploads/pic_floor02_1@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor02_2@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor02_3@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor02_4@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor03_5@2x.png" alt="">
          </a>
        </div>
      </div>
      <div class="floor">
        <!-- 标题 -->
        <div class="title">
          <img src="/static/uploads/pic_floor03_title.png" alt="">
        </div>
        <!-- 分类 -->
        <div class="items">
          <a href="">
            <img src="/static/uploads/pic_floor03_1@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor03_2@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor03_3@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor03_4@2x.png" alt="">
          </a>
          <a href="">
            <img src="/static/uploads/pic_floor03_5@2x.png" alt="">
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  // 导入 自定义搜索组件
  import search from '@/components/search';

  export default {

    data () {
      return {
        windowHeight: 'auto'
      }
    },

    // 注册组件
    components: {
      search
    },

    methods: {
      disableScroll (ev) {
        // console.log(ev);
        this.windowHeight = ev.windowHeight;
      }
    }
  }
</script>

<style scoped lang="less">

  // 焦点图
  .banner {
    height: 340rpx;

    a {
      display: block;
      height: 340rpx;
    }
  }

  // 主导航
  .navs {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 192rpx;
    padding: 0 36rpx;
    // background-color: pink;

    a {
      width: 128rpx;
      height: 140rpx;
    }
  }

  // 楼层
  .floor {

    .title {
      width: 750rpx;
      height: 60rpx;
      padding: 30rpx 0 0 15rpx;
      background-color: #f4f4f4;
    }

    .items {
      padding: 20rpx 16rpx;
      overflow: hidden;

      a {
        float: left;
        margin-left: 10rpx;
        
        // 前两个
        // 0 --> 2  1 --> 1  2 --> 0
        // &:nth-child(-n+2) {}

        &:nth-last-child(-n+2) {
          margin-top: 10rpx;
        }

        &:first-child {
          width: 232rpx;
          height: 386rpx;
          margin-left: 0;
        }

        &:nth-child(2),
        &:nth-child(5) {
          width: 273rpx;
          height: 188rpx;
        }

        &:nth-child(3),
        &:nth-child(4) {
          width: 193rpx;
          height: 188rpx;
        }
      }
    }

    &:first-child {
    
      a {
        width: 233rpx !important;
        height: 188rpx;
      }
    }
  }
</style>
