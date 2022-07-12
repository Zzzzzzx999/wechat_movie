<template>
  <div class="result">
    <span>{{keyWord}}</span>
    <div class="pageNavigation" v-show="a">
        <ul>
            <li v-for="film in selectList" :key="film.id">
                <div class="photo">
                    <img :src="film.img" alt="" mode="aspectFill">
                      <div class="filmScore">
                        <span>{{film.score}}</span>
                    </div>
                </div>
                <span>{{film.name}}</span>
                <div class="filmTypes">
                    <button size="mini" v-for="(type,index) in film.type" :key="index">{{type}}</button>
                </div>
            </li>
        </ul>
    </div>
    <div class="notFound" v-show="!a">
        <img src="../static/my/M-搜索不到.png" mode="aspectFill" alt="" />
        <span>亲,找不到你想要的电影</span>
        <button>逛逛其他电影</button>
    </div>
  </div>
</template>

<script>
export default {
    name:'searchResult',
    data() {
      return {
        allList:[
          {id: 1,name:'健听女孩',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/eaf81a4c510fd9f9d72a89c86966c32a2834349b0e74?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'8.6分'},
          {id: 2,name:'杰伊·比姆',type:['剧情','犯罪'],img:"https://img0.baidu.com/it/u=3158986335,2577920955&fm=253&fmt=auto&app=120&f=JPEG?w=500&h=750",score:'8.7分'},
          {id: 3,name:'最后的决斗',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/ca1349540923dd54564ebf768d5ba4de9c82d158e229?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'8.4分'},
          {id: 4,name:'倒数时刻',type:['爱情','动作'],img:"https://bkimg.cdn.bcebos.com/pic/14ce36d3d539b6003af3e7698c01222ac65c113819e9?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
          {id: 5,name:'打开心世界',type:['爱情'],img:"https://bkimg.cdn.bcebos.com/pic/0df3d7ca7bcb0a46f21fefd7b228e1246b600d330183?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto",score:'8.2分'},
          {id: 6,name:'玫瑰岛的历史',type:['喜剧'],img:"https://bkimg.cdn.bcebos.com/pic/d058ccbf6c81800a19d84aeb2d7824fa828ba71ee98a?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.0分'},
          {id: 7,name:'千与千寻',type:['剧情','动画'],img:"https://bkimg.cdn.bcebos.com/pic/bd3eb13533fa828ba61ea8fe6a4e5634970a304eecd7?x-bce-process=image/resize,m_lfit,h_500,limit_1/format,f_auto",score:'8.2分'},
          {id: 8,name:'雄狮少年',type:['喜剧'],img:"https://bkimg.cdn.bcebos.com/pic/a50f4bfbfbedab64034f27728b64b8c379310a55b07d?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
          {id: 9,name:'孤味',type:['剧情','家庭','亲情'],img:"https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2623646280.webp",score:'8.0分'},
          {id: 10,name:'悬崖之上',type:['动作','剧情'],img:"https://bkimg.cdn.bcebos.com/pic/37d3d539b6003af33a872eeb4966d15c1038524318a1?x-bce-process=image/resize,m_lfit,h_500,limit_1/format,f_auto",score:'8.4分'},
          {id: 11,name:'吉祥如意',type:['家庭','家庭'],img:"https://bkimg.cdn.bcebos.com/pic/eaf81a4c510fd9f9d72a89c86966c32a2834349b0e74?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'7.8分'},
          {id: 12,name:'扬名立万',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/e61190ef76c6a7efce1b4e6e5daab851f3deb48fc860?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg",score:'8.5分'},
          {id: 13,name:'摆渡人',type:['喜剧','爱情'],img:"https://bkimg.cdn.bcebos.com/pic/0bd162d9f2d3572c15ecb3e78313632762d0c3fa?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyMjA=,g_7,xp_5,yp_5/format,f_auto",score:'暂无评分'},
          {id: 14,name:'战狼2',type:['动作','战争','军事'],img:"https://bkimg.cdn.bcebos.com/pic/8694a4c27d1ed21b84c524bea76eddc451da3f58?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxODA=,g_7,xp_5,yp_5/format,f_auto",score:'7.5分'},
          {id: 15,name:'肖申克的救赎',type:['剧情'],img:"https://bkimg.cdn.bcebos.com/pic/38dbb6fd5266d016092478b8667ac30735fae6cd9f5b?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxMTY=,g_7,xp_5,yp_5/format,f_auto",score:'9.7分'},
          {id: 16,name:'泰坦尼克号2',type:['动作','爱情'],img:"https://bkimg.cdn.bcebos.com/pic/7af40ad162d9f2d3f6646a5fa3ec8a136327cc0d?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U4MA==,g_7,xp_5,yp_5/format,f_auto",score:'9.4分'},
          {id: 17,name:'当幸福来敲门',type:['家庭','传记'],img:"https://bkimg.cdn.bcebos.com/pic/e1fe9925bc315c6026eed9bd8fb1cb134954776c?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto",score:'9.3分'},
          {id: 18,name:'红海行动',type:['动作'],img:"https://bkimg.cdn.bcebos.com/pic/48540923dd54564e6348769db8de9c82d1584f61?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxODA=,g_7,xp_5,yp_5/format,f_auto",score:'8.3分'},
        ],
        selectList:[],
        a:true, //判断是否有存在用户搜素的电影
        b:0, //通过关键词筛选出来的电影总数
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

    onLoad(query) {
      wx.setNavigationBarTitle({title: query.keyWord})
      this.allList.forEach((film)=>{
        if(film.name.indexOf(query.keyWord)>=0){
          this.selectList.unshift(film)
          this.b++
          console.log('通过电影名称筛选电影')
        }else if(film.type.indexOf(query.keyWord)>=0){
          this.selectList.unshift(film)
          console.log('通过电影类型筛选电影');
          this.b++
        }
      })
      if(this.b===0){
        this.a=false
        console.log(this.a);
      }
      console.log('@@@@@@@@@@',this.b);
      console.log('@@@@@@@@@@',this.a);
      // this.selectList=this.allList.name.indexOf(query.keyWord)
    },
    /* mounted() {
      this.$bus.$on('getKeyWord',(keyWord)=>{
          console.log('我是searchResult,收到了数据',keyWord);
      })
    },
    beforeDestroy() {
      this.$bus.$off('getKeyWord')
    }, */
}
</script>

<style>
ul{
  display: flex;
  align-items:center;
  flex-direction: row;
  justify-content: flex-start;
  flex-wrap: wrap;
  width: 100vw;
  height: 100%;
  margin-bottom: 50rpx;
}
ul li{
  width: 340rpx;
  height: 640rpx;
  background-color: white;
  margin: 28rpx 16rpx;
  border: 1px solid #DDDDDD;
  border-radius: 15rpx;
}
.result{
  height: 90vh;
  width: 100vw;
}
.notFound {
  display: flex;
  flex-flow: column wrap;
  justify-content: space-around;
  align-items: center;
  height: 50%;
  width: 100%;
}
.notFound img{
  max-width: 150rpx;
  max-height: 150rpx;
}
.notFound button{
  border: 2rpx solid #8FBC8F;
  color: #8FBC8F;
}
.pageNavigation button{
  margin-right: 25rpx !important;
}
</style>