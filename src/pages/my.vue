<template>
  <div class="myself">
        <div class="header">
            <div class="bgcimage">
                <img src="../static/apic38401_s.jpg" alt="">
            </div>  
            <div class="myInfo">
                <img src="https://img0.baidu.com/it/u=152502135,3087038181&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500" alt="">
                <div class="name">
                    <span>{{userInfo.name}}</span>
                    <img class="sex" src="../static/my/男.png" alt=""><br>
                </div>
                <div class="userfrom">
                    <span>Fujian,Xiamen</span>
                </div>
            </div>
            <div class="myskin" @click="mySkinPath">
                <img src="../static/icons/皮肤.png" alt="">
            </div>
        </div>
        <div class="functionalArea">
            <div class="favorate functional" @click="favoritePath">
                <div class="space">
                    <img src="../static/icons/收藏.png" alt="">
                    <span>收藏</span>
                </div>
            </div>
            <div class="history functional" @click="historyPath">
                <div class="space">
                    <img src="../static/icons/浏览记录.png" alt="">
                    <span>浏览记录</span>
                </div>
            </div>
            <div class="shake functional" @click="shakePath">
                <div class="space">
                    <img src="../static/icons/摇一摇.png" alt="">
                    <span>摇一摇</span>
                </div>
            </div>
            <div class="gallery functional" @click="galleryPath">
                <div class="space">
                    <img src="../static/icons/相册.png" alt="">
                    <span>相册</span>
                </div>
            </div>
            <div class="setting functional" @click="btnPath('/pages/setting')">
                <div class="space">
                    <img src="../static/icons/设置.png" alt="">
                    <span>设置</span>
                </div>
            </div>
        </div>
        <!-- <div class="pageFooter">
            <div class="bannerItem" @click="popularPath()">
                <div class="bannerSpace">
                    <img src="../static/icons/电影(1).png" alt="">
                    <span>热映</span>
                </div>
            </div>
            <div class="bannerItem" @click="comingPath()">
                <div class="bannerSpace">
                    <img src="../static/icons/电影(3).png" alt="">
                    <span>待映</span>
                </div>
            </div>
            <div class="bannerItem" @click="topPath()">
                <div class="bannerSpace">
                    <img src="../static/icons/口碑(1).png" alt="">
                    <span>口碑</span>
                </div>
            </div>
            <div class="bannerItem">
                <div class="bannerSpace">
                    <img src="../static/icons/我的.png" alt="">
                    <span>我的</span>
                </div>
            </div>
        </div> -->
  </div>
</template>

<script>
export default {
    name:'my',

    data() {
        return{
            userInfo: {
                name: 'Sesine'
            }
        }
    },

    onLoad() {
    },

    onShow() {
        if (wx.getStorageSync('userInfo')) {
            this.userInfo = wx.getStorageSync('userInfo')
        }
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

    methods: {
        /* popularPath(){
            uni.navigateTo({url: '/pages/popular'})
        },
        topPath(){
            uni.navigateTo({url: '/pages/top'})
        },
        comingPath(){
            uni.navigateTo({url: '/pages/coming'})
        }, */
        shakePath(){
            uni.navigateTo({url: '/pages/shake'})
        },
        favoritePath(){
            uni.navigateTo({url: '/pages/favorite'})
        },
        historyPath(){
            uni.navigateTo({url: '/pages/history'})
        },
        galleryPath(){
            uni.navigateTo({url: '/pages/gallery'})
        },
        settingPath(){
            uni.navigateTo({url: '/pages/setting'})
        },
        mySkinPath(){
            uni.navigateTo({url:'/pages/myskin'})
        },
        btnPath(url){
            uni.navigateTo({url:url})
        }
    }
}
</script>

<style>
    .header{
        position: relative;
        height: 35vh;
        width: 100vw;
    }
    .header .bgcimage{
        height: 100%;
        width: 100%;
        z-index: -666;
    }
    .header .bgcimage img{
        width: 100%;
        height: 100%;
    }
    .header .myskin{
        position: absolute;
        top: 10%;
        right: 5%;
        max-width: 150rpx;
        max-height: 150rpx;
    }
    .header .myskin img{
        width: 60rpx;
        height: 60rpx;
    }
    .myInfo{
        position: absolute;
        text-align: center;
        left: 50%;
        top: 56%;
        transform: translate(-50%,-50%);
    }
    .myInfo img{
        border-radius: 50%;
        max-width: 150rpx;
        max-height: 150rpx;
    }
    .myInfo .sex{
        max-width: 40rpx;
        max-height: 40rpx;
        padding: 0 10rpx;
    }
    .myInfo .name{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .myInfo .name span{
        color: aliceblue;
    }
    .myInfo .userfrom{
        margin: 10rpx 0;
    }
    .myInfo .userfrom span{
        color: aliceblue;
        font-size: smaller;
    }
    .functionalArea{
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-flow: row wrap;
        /* border-left: 1rpx solid grey;
        border-bottom: 1rpx solid grey; */
    }
    .functional{
        position: relative;
        width: 33.3%;
        height: 200rpx;
        text-align: center;
        border-top: 1rpx solid grey;
        border-right: 1rpx solid grey;
        box-sizing: border-box;
    }
    /* .functional:nth-last-child(1){
        border-bottom: 1rpx solid grey;
    }
    .functional:nth-last-child(2){
        border-bottom: 1rpx solid grey;
    } */
    .functional:nth-last-of-type(-n + 3){
        border-bottom: 1rpx solid grey;
    }
    .functional img{
        width: 65rpx;
        height: 65rpx;
    }
    .functional span{
        font-family: Arial, Helvetica, sans-serif;
        font-size: 30rpx;
        padding-top: 30rpx;
        font-weight: 500;
    }
    .space{
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
        align-items: center;
        position: absolute;
        left: 50%;
        top: 50%;
        height: 130rpx;
        width: 119rpx;
        transform: translate(-50%,-50%);
    }
</style>