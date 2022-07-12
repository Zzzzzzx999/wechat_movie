<template>
  <div class="">
    <div class="pageNavigation">
        <ul>
          <li v-for="film in comingFilms" :key="film.id">
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
        <div class="bannerItem" @click="popularPath()">
            <div class="space">
              <img src="../static/icons/电影(1).png" alt="">
              <span>热映</span>
            </div>
        </div>
        <div class="bannerItem">
            <div class="space">
              <img src="../static/icons/电影(2).png" alt="">
              <span>待映</span>
            </div>
        </div>
        <div class="bannerItem" @click="topPath()">
            <div class="space">
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
    name:'coming',
    data() {
      return {
        comingFilms:[
          {id: 1,name:'千与千寻',type:['剧情','动画'],img:"https://bkimg.cdn.bcebos.com/pic/bd3eb13533fa828ba61ea8fe6a4e5634970a304eecd7?x-bce-process=image/resize,m_lfit,h_500,limit_1/format,f_auto",score:'8.2分'},
          {id: 2,name:'雄狮少年',type:['喜剧'],img:"https://bkimg.cdn.bcebos.com/pic/a50f4bfbfbedab64034f27728b64b8c379310a55b07d?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
          {id: 3,name:'孤味',type:['剧情','家庭','亲情'],img:"https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2623646280.webp",score:'8.0分'},
          {id: 4,name:'悬崖之上',type:['动作','剧情'],img:"https://bkimg.cdn.bcebos.com/pic/37d3d539b6003af33a872eeb4966d15c1038524318a1?x-bce-process=image/resize,m_lfit,h_500,limit_1/format,f_auto",score:'8.4分'},
          {id: 5,name:'吉祥如意',type:['家庭','家庭'],img:"https://bkimg.cdn.bcebos.com/pic/eaf81a4c510fd9f9d72a89c86966c32a2834349b0e74?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'7.8分'},
          {id: 6,name:'扬名立万',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/e61190ef76c6a7efce1b4e6e5daab851f3deb48fc860?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'8.5分'},
        ]
      }
    },
    methods: {
        /* popularPath(){
            uni.navigateTo({url: '/pages/popular'})
        },
        topPath(){
            uni.navigateTo({url: '/pages/top'})
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