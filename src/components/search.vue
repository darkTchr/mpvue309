
<template>
  <!-- 搜索框 -->
  <div class="search" :class="{focused: focused}">
    <!-- 输入框 -->
    <div class="input-box">
      <input @focus="goSearch" type="text" :placeholder="placeholder">
      <p class="cancel" @click="cancelSearch">取消</p>
    </div>
    <!--  -->
    <div class="content"></div>
  </div>
</template>

<script>

  export default {

    data () {
      return {
        focused: false,
        placeholder: ''
      }
    },

    methods: {
      goSearch () {
        // 添加 focused 这个类名
        this.focused = true;
        // 设置占位符
        this.placeholder = '请输入您想要的商品';

        // 动态获取屏幕的可用高度
        const {windowHeight} = wx.getSystemInfoSync();

        // console.log(windowHeight)

        // 触发父组件事件，并传值
        this.$emit('search', {
          windowHeight: windowHeight + 'px'
        })
      },

      cancelSearch () {
        // 添加 focused 这个类名
        this.focused = false;
        // 移除占位符
        this.placeholder = '';

        // 触发父组件事件，并传值
        this.$emit('search', {
          windowHeight: 'auto'
        })
      }
    }
  }

</script>

<style lang="less">
  // 搜索
  .search {
    padding: 20rpx 30rpx;
    background-color: #ea4451;

    .input-box {
      position: relative;
      display: flex;

      &::before {
        content: '';
        position: absolute;
        display: none;
        left: 0;
        top: 50%;
        width: 32rpx;
        height: 32rpx;
        transform: translate(20rpx, -50%);
        background-image: url(https://zhaorq7.github.io/mpResource309/images/icon_search@2x.png);
        background-size: auto 32rpx;
      }

      &::after {
        content: '搜索';
        position: absolute;
        left: 50%;
        top: 50%;
        height: 32rpx;
        line-height: 32rpx;
        padding-left: 50rpx;
        transform: translate(-50%, -50%);
        font-size: 24rpx;
        color: #bbb;
        background-image: url(https://zhaorq7.github.io/mpResource309/images/icon_search@2x.png);
        background-size: auto 32rpx;
        background-repeat: no-repeat;
      }
    }

    input {
      height: 60rpx;
      padding-left: 60rpx;
      background-color: #fff;
      border-radius: 10rpx;
      flex: 1;
      font-size: 27rpx;
      color: #808080;
    }

    .cancel {
      display: none;
      width: 100rpx;
      line-height: 60rpx;
      text-align: right;
      color: #333;
      font-size: 30rpx;
    }

    .content {
      position: absolute;
      left: 0;
      right: 0;
      top: 100rpx;
      bottom: 0;
      background-color: #fff;
      display: none;
    }

    //
    &.focused {
      position: absolute;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      z-index: 9;

      background-color: #eee;

      .input-box {

        &::before {
          display: block;
        }

        &::after {
          display: none;
        }
      }

      .cancel {
        display: block;
      }

      .content {
        display: block;
      }
    }
  }
</style>
