<template>
    <div class="systemInfo">
        <div class="infoItem">
            <span>手机型号</span> 
            <text style="text-align:right">iPhone 6</text>
        </div>
        <div class="infoItem">
            <span>分辨率</span> 
            <text style="text-align:right">750*1206</text>
        </div>
        <div class="infoItem">
            <span>系统语言</span> 
            <text style="text-align:right">zh_CN</text>
        </div>
        <div class="infoItem">
            <span>微信版本</span> 
            <text style="text-align:right">6.5.2</text>
        </div>
        <div class="infoItem">
            <span>小程序版本</span> 
            <text style="text-align:right">v2.0</text>
        </div>
    </div>
</template>

<script>
export default {
    name:'systemInfo',
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
body{
    background-color: whitesmoke;
}
.infoItem{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding: 0 35rpx;
    background-color: white;
    height: 80rpx;
    border-bottom: 1rpx solid rgb(240, 239, 239);
}
.infoItem span{
    text-align: left;
    font-size: 36rpx;
    font-weight: 600;
    width: 29%;
}
.infoItem text{
    width: 71%;
    text-align: left;
    color: rgb(161, 161, 161);
    font-size: 32rpx;
}

.saveInfo{
    margin: 150rpx 200rpx 0 200rpx;
}
button{
    background-color: #8FBC8F;
}
.otherInfo{
    margin-top: 20rpx;
}
.personalSignature{
    margin-top: 20rpx;
}
</style>