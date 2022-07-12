<template>
    <div>
        <div class="search">
            <img src="../static/search.png" alt="">
            <input type="text" placeholder="请输入关键词搜索" @click="searchPath">
        </div>
        <!-- 页面操作向导 -->
        <div class="pageSectionSwiper">
            <swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
                <swiper-item>
                    <view class="swiper-item">
                        <image mode="widthFix" src="https://bkimg.cdn.bcebos.com/pic/e1fe9925bc315c6026eed9bd8fb1cb134954776c?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto" alt="">
                    </view>
                </swiper-item>
                <swiper-item>
                    <view class="swiper-item">
                        <image mode="widthFix" src="https://bkimg.cdn.bcebos.com/pic/d058ccbf6c81800a19d84aeb2d7824fa828ba71ee98a?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto" alt="">
                    </view>
                </swiper-item>
                <swiper-item>
                    <view class="swiper-item">
                        <image mode="widthFix" src="https://bkimg.cdn.bcebos.com/pic/37d3d539b6003af33a872eeb4966d15c1038524318a1?x-bce-process=image/resize,m_lfit,h_500,limit_1/format,f_auto" alt="">
                    </view>
                </swiper-item>
            </swiper>
        </div>
        <!-- 页面导航图 -->
        <div class="pageNavigation">
            <ul>
                <li v-for="film in popularFilms" :key="film.id">
                    <div class="photo">
                        <img :src="film.img" alt="" mode="aspectFill">
                         <div class="filmScore">
                            <span>{{film.score}}</span>
                        </div>
                    </div>
                    <span>{{film.name}}</span>
                    <div class="filmTypes">
                        <div id="types" v-for="(type,index) in film.type" :key="index">{{type}}</div>
                    </div>
                </li>
            </ul>
        </div>
        <!-- <div class="pageFooter">
            <div class="bannerItem" >
                <div class="space">
                    <img src="../static/icons/电影.png" alt="">
                    <span>热映</span>
                </div>
            </div>
            <div class="bannerItem" @click="comingPath()">
                <div class="space">
                    <img src="../static/icons/电影(1).png" alt="">
                    <span>待映</span>
                </div>
            </div>
            <div class="bannerItem" @click="topPath()">
                <div class="sapce">
                    <img src="../static/icons/口碑(1).png" alt="">
                    <span>口碑</span>
                </div>
            </div>
            <div class="bannerItem" @click="myPath()">
                <div class="space">
                    <img src="../static/icons/我的(1).png" alt="">
                    <span>我的</span>
                </div>
            </div>
        </div> -->
    </div>
</template>

<script>
export default {
    name:'popular',
    data() {
        return {
            indicatorDots: true,  //是否显示面板指示点
            autoplay: true, //是否自动切换
            interval: 2000, //自动切换时间间隔
            duration: 500,   //滑动动画时长
            popularFilms:[
                {id: 1,name:'健听女孩',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/eaf81a4c510fd9f9d72a89c86966c32a2834349b0e74?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'8.6分'},
                {id: 2,name:'杰伊·比姆',type:['剧情','犯罪'],img:"https://img0.baidu.com/it/u=3158986335,2577920955&fm=253&fmt=auto&app=120&f=JPEG?w=500&h=750",score:'8.7分'},
                {id: 3,name:'最后的决斗',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/ca1349540923dd54564ebf768d5ba4de9c82d158e229?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'8.4分'},
                {id: 4,name:'倒数时刻',type:['动作','爱情'],img:"https://bkimg.cdn.bcebos.com/pic/14ce36d3d539b6003af3e7698c01222ac65c113819e9?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
                {id: 5,name:'打开心世界',type:['爱情'],img:"https://bkimg.cdn.bcebos.com/pic/0df3d7ca7bcb0a46f21fefd7b228e1246b600d330183?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto",score:'8.2分'},
                {id: 6,name:'玫瑰岛的历史',type:['喜剧'],img:"https://bkimg.cdn.bcebos.com/pic/d058ccbf6c81800a19d84aeb2d7824fa828ba71ee98a?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.0分'},
                {id: 7,name:'千与千寻',type:['剧情','动画'],img:"https://bkimg.cdn.bcebos.com/pic/bd3eb13533fa828ba61ea8fe6a4e5634970a304eecd7?x-bce-process=image/resize,m_lfit,h_500,limit_1/format,f_auto",score:'8.2分'},
                {id: 8,name:'雄狮少年',type:['喜剧'],img:"https://bkimg.cdn.bcebos.com/pic/a50f4bfbfbedab64034f27728b64b8c379310a55b07d?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
            ],
            list: [
                {id: 3,name:'最后的决斗',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/ca1349540923dd54564ebf768d5ba4de9c82d158e229?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'8.4分'},
                {id: 4,name:'倒数时刻',type:['动作','爱情'],img:"https://bkimg.cdn.bcebos.com/pic/14ce36d3d539b6003af3e7698c01222ac65c113819e9?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
                {id: 5,name:'打开心世界',type:['爱情'],img:"https://bkimg.cdn.bcebos.com/pic/0df3d7ca7bcb0a46f21fefd7b228e1246b600d330183?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto",score:'8.2分'},
                {id: 6,name:'玫瑰岛的历史',type:['喜剧'],img:"https://bkimg.cdn.bcebos.com/pic/d058ccbf6c81800a19d84aeb2d7824fa828ba71ee98a?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.0分'},
            ]
        }
    },
    methods: {
        /* comingPath(){
            uni.navigateTo({url: '/pages/coming'})
        },
        topPath(){
            uni.navigateTo({url: '/pages/top'})
        },
        myPath(){
            uni.navigateTo({url: '/pages/my'})
        }, */
        searchPath(){
            uni.navigateTo({url: '/pages/search'})
        }
    },

    // 下拉刷新
    onPullDownRefresh() {
        // this.popularFilms = []
        // wx.stopPullDownRefresh()
    },

    // 上拉加载
    onReachBottom() {
        wx.showLoading({
            title:'加载中'
        })
        setTimeout(() => {
            this.popularFilms = this.popularFilms.concat(this.list)
            wx.hideLoading()
        }, 2000);
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
    /* mounted() {
        this.$bus.$emit('popularFilms',this.popularFilms)
    }, */
}
</script>

<style>
    ul{
        display: flex;
        align-items:center;
        flex-direction: row;
        justify-content: space-around;
        flex-wrap: wrap;
        width: 100vw;
    }
    ul li{
        width: 340rpx;
        height: 640rpx;
        background-color: white;
        margin: 28rpx 0;
        border: 1px solid #DDDDDD;
        border-radius: 15rpx;
    }
    .search{
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
    }
    .search img{
        height: 60rpx;
        width: 60rpx;
        position: absolute;
        left: 3%;
        top: 24%;
    }
    input{
		display: flex;
        align-items: center;
        justify-content: center;
		border: 1px solid #2aabd2;
  		border-radius: 3px;
        width:95%;
        text-align: center;
        margin: 20rpx 20rpx 0 20rpx;
        height: 70rpx;
        background-color: white;
        font-size: 33rpx;
	}
    .pageSectionSwiper{
        margin: 20rpx 0;
        height: 380rpx;
        width: 750rpx;
    }
    .pageSectionSwiper .swiper{
        height: 380rpx;
        width: 750rpx;
    }
    .swiper-item{
        height: 100%;
        text-align: center;
    }
    .swiper-item image{
        display: inline-block;
        overflow: hidden;
        height: 380rpx;
        width: 750rpx;
    }


    



    /* ul{
        display: flex;
        align-items:center;
        flex-direction: row;
        justify-content: space-around;
        flex-wrap: wrap;
        width: 99vw;
        padding-bottom: 60rpx;
    }
    li{
        width: 340rpx;
        height: 700rpx;
        padding: 15rpx 15rpx 50rpx ;
    }
    li span{
        padding:20rpx;
        font-size: 35rpx;
        font-family: Arial, Helvetica, sans-serif;
        font: bolder;
    }
    img{
        width: 100%;
    }
    button{
        padding: 0 5px;
    }
    .pageFooter{
        display: flex;
        height: 50px;
        width: 100vw;
        position: fixed;
        bottom: 0%;
        z-index: 999;
        background-color: whitesmoke;
    }
    .bannerItem{
        height: 50rpx;
        width: 100vw;
    }
    .bannerItem img{
        width: 100%;
        height: 100%;
        max-height: 70rpx;
        max-width: 70rpx;
    }
    .bannerItem span{
        display: flex;
        justify-content: space-around;
        align-items: center;
        font-size: 32rpx;
    } */
</style>