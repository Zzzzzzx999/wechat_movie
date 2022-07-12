<template>
    <div class="mySetting">
        <div class="settingItem personalData" @click="personInfoPath">
            <span>个人资料</span>
            <img src="../static/icons/箭头.png" alt="">
        </div>
        <div class="settingItem phoneInfomation" @click="systemInfoPath">
            <span>手机信息</span>
            <img src="../static/icons/箭头.png" alt="">
        </div>
        <div class="settingItem cacheCleaner" @click="cacheCleaner">
            <span>清理缓存</span>
            <img src="../static/icons/箭头.png" alt="">
        </div>
        <div class="settingItem updateLocation" @click="updateLocation">
            <span>更新位置</span>
            <img src="../static/icons/箭头.png" alt="">
        </div>
        <div class="settingItem about" @click="about">
            <span>关于</span>
            <img src="../static/icons/箭头.png" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name:'setting',
    methods: {
        cacheCleaner(){
            wx.showModal({
                title: '确认要清除',
                content: '清除缓存会删除浏览历史和收藏及个人资料',
                success (res) {
                    if (res.confirm) {
                        wx.clearStorage()
                        console.log('用户点击确定')
                    } else if (res.cancel) {
                        console.log('用户点击取消')
                    }
                }
            })
            console.log('@@@@');
        },
        personInfoPath(){
            wx.navigateTo({url: './personInfo'})
        },
        systemInfoPath(){
            wx.navigateTo({url:'./systemInfo'})
        },
        updateLocation(){
            wx.navigateTo({url:'./location'})
        },
        about(){
            wx.navigateTo({url:'./about'})
        }
    }, 
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
.mySetting{
    display: flex;
    justify-content: flex-start;
    flex-flow: column;
    background-color: whitesmoke;
    height: 100vh;
    width: 100vw;
}
.settingItem{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    position: relative;
    height: 40px;
    background-color: white;
    margin: 10rpx 0;
}
.settingItem span{
    padding-left: 30rpx;
}
.settingItem img{
    position: absolute;
    right: 22rpx;
    height: 40%;
    width: 10%;
}
</style>