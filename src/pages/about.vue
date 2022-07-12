<template>
    <div class="about">
        <div class="title">
            <span>电影推荐</span>
        </div>
        <div class="content">
            <div class="backEndSupport item">
                <span>后端支持</span>
                <text>豆瓣API:https://developers.douban.com/</text>
                <text>百度地图API:http://lbsyun.bai.com/</text>
            </div>
            <div class="author item">
                <span>作者</span>
                <text>sesine:https://github.com/yesifeng</text>
            </div>
            <div class="usedAPI item">
                <span>在此项目所用到的API</span>
                <text>wx.request、WX.chooselmage、wx.previewlmage、wx.playVoice、wx.saveFile、wx.setStorage、wx.loginWX、.getStorage、
                    wx.clearStorage、wx.showToast、wx.getStoragelnfo、wx.getLocation、wx.getSysteminfo、wx.onAccelerometerChange、
                    wx.showModal、wx.showActionSheet、wx.setNavigationBarTitle、wx.navigateTo、wx.redirectTo</text>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'about',
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
    .title{
        font-size: 60rpx;
        text-align: center;
        margin: 50rpx;
    }
    .content{
        margin: 120rpx 50rpx 0 50rpx;
    }
    .content span{
        color: black;
        font-size: 43rpx;
        margin: 20rpx 0;
        text-align: left;
        font-weight: 600;
        width: 100%;
    }
    .content text{
        color: rgb(170, 169, 169);
        font-size: 31rpx;
    }
    .item{
        display: flex;
        align-items: center;
        flex-flow: row wrap;
        margin: 30rpx;
    }
</style>