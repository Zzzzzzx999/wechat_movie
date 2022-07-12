<template>
  <div class="shakePhone">
      <img mode="aspectFill" src="https://img1.baidu.com/it/u=3005595915,3368651875&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=595" alt="">
      <span>摇一摇，发现好电影</span>
  </div>
</template>

<script>
export default {
    name:'shake',
    onShow: function() {
        console.log('App Show')
        console.log(this.background);
        if (wx.getStorageSync('background')) {
            this.background = wx.getStorageSync('background')
            this.bgcolor=this.background.color
        }
        wx.setNavigationBarColor({      // 窗口的背景色
            frontColor: '#000000',
            backgroundColor: this.bgcolor
        });
        wx.setBackgroundColor({
            backgroundColor: this.bgcolor, // 窗口的背景色为白色
        })
    },
}
</script>

<style>
    .shakePhone{
        position: relative;
        background-color: gainsboro;
        width: 100vw;
        height: 100vh;
    }
    img{
        width: 100vw;
        height: 100vh;
        opacity: 0.7;
    }
    span{
        position: absolute;
        top: 20%;
        left: 50%;
        transform: translate(-50%,-50%);
        color: black;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-weight: bolder;
        font-size: 40rpx;
    }
</style>