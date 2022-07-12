<template>
  <div class="top">
    <div class="pageNavigation">
        <ul>
            <li v-for="film in topFilms" :key="film.id">
                <div class="photo">
                    <img :src="film.img" mode="aspectFill" alt="" webp=true>
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
        <div class="bannerItem" @click="popularPath()">
            <div class="space">
                <img src="../static/icons/电影(1).png" alt="">
                <span>热映</span>
            </div>
        </div>
        <div class="bannerItem" @click="comingPath()">
            <div class="space">
                <img src="../static/icons/电影(3).png" alt="">
                <span>待映</span>
            </div>
        </div>
        <div class="bannerItem">
            <div class="space">
                <img src="../static/icons/口碑.png" alt="">
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
    name:'top',
    data() {
      return {
        topFilms:[
          {id: 1,name:'摆渡人',type:['喜剧','爱情'],img:"https://bkimg.cdn.bcebos.com/pic/0bd162d9f2d3572c15ecb3e78313632762d0c3fa?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyMjA=,g_7,xp_5,yp_5/format,f_auto",score:'暂无评分'},
          {id: 2,name:'战狼2',type:['动作','战争','军事'],img:"https://bkimg.cdn.bcebos.com/pic/8694a4c27d1ed21b84c524bea76eddc451da3f58?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxODA=,g_7,xp_5,yp_5/format,f_auto",score:'7.5分'},
          {id: 3,name:'肖申克的救赎',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/38dbb6fd5266d016092478b8667ac30735fae6cd9f5b?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxMTY=,g_7,xp_5,yp_5/format,f_auto",score:'9.7分'},
          {id: 4,name:'泰坦尼克号2',type:['动作','爱情'],img:"https://bkimg.cdn.bcebos.com/pic/7af40ad162d9f2d3f6646a5fa3ec8a136327cc0d?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U4MA==,g_7,xp_5,yp_5/format,f_auto",score:'9.4分'},
          {id: 5,name:'当幸福来敲门',type:['家庭','传记'],img:"https://bkimg.cdn.bcebos.com/pic/e1fe9925bc315c6026eed9bd8fb1cb134954776c?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto",score:'9.3分'},
          {id: 6,name:'红海行动',type:['动作'],img:"https://bkimg.cdn.bcebos.com/pic/48540923dd54564e6348769db8de9c82d1584f61?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxODA=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
        ]
      }
    },
    methods: {
        /* popularPath(){
            uni.navigateTo({url: '/pages/popular'})
        },
        comingPath(){
            uni.navigateTo({url: '/pages/coming'})
        },
        myPath(){
            uni.navigateTo({url: '/pages/my'})
        }, */
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
</style>