<template>
  <div class="userHistory">
    <div class="historyList">
        <!-- changeChannel -->
        <div class="historyMovie" :class="{'active':a}" @click="changeMovieChannel">
            <span>电影</span>
        </div>
        <div class="historyPerson" :class="{'active':!a}" @click="changePersonChannel">
            <span>人物</span>
        </div>
    </div>
    <div class="showArea">
      <div class="historyMovieShow" v-show="a">
        <div class="movieShow" v-show="b">
          <ul>
            <li v-for="film in historyMovie" :key="film.id">
              <div class="watchTime">
                <span>22:26:32</span>
              </div>
              <div class="movie">
                <div class="moviePhoto">
                  <img :src="film.src" alt="" mode="aspectFill">
                </div>
                <div class="movieInfo">
                  <div class="infoItem" id="title">{{film.name}}</div><br>
                  <div class="infoItem">导演:{{film.director}}</div><br>
                  <div class="infoItem" id="actor">演员:{{film.performer}}</div><br>
                  <div class="infoItem">豆瓣评分:{{film.score}}</div><br>
                  <div class="infoItem">上映年份:{{film.releaseDate}}</div><br>
                </div>
              </div>
            </li>
          </ul>
        </div>
        <div class="notFound" v-show="!b">
          <img src="../static/my/M-搜索不到.png" alt="" />
          <span>亲,找不到电影的收藏</span>
          <button>去逛逛</button>
        </div>
      </div>
      <div class="historyPersonShow" v-show="!a">
        <div class="personShow" v-show="c">
          <span id="data">2022-4-22</span>
          <span id="data">22:15:26</span>
          <ul>
            <li v-for="person in historyPerson" :key="person.id">
              <div class="personImg">
                <img :src="person.personImg" alt="" mode="aspectFill">
              </div>
              <div class="personInfo">
                <span id="title">{{person.name}}</span><br>
                <span>{{person.EnglishName}}</span><br>
                <span>{{person.address}}</span><br>
                <span>主要作品:{{person.works}}</span>
              </div>
            </li>
          </ul>
        </div>
        <div class="notFound" v-show="!c">
            <img src="../static/my/M-搜索不到.png" alt="" />
            <span>亲,找不到人物的收藏</span>
            <button>去逛逛</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "history",
  data() {
      return {
          a:true,
          b:true,
          c:true,
          historyMovie:[
            {id:1,name:'摆渡人',director:'张嘉佳',performer:'梁朝伟/金城武/陈奕迅/杨颖',score:'暂无评分',releaseDate:'2016',src:'https://bkimg.cdn.bcebos.com/pic/0bd162d9f2d3572c15ecb3e78313632762d0c3fa?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyMjA=,g_7,xp_5,yp_5/format,f_auto'},
            {id:2,name:'血战钢锯岭',director:'梅尔·吉布森',performer:'安德鲁·加菲尔德/萨姆·沃辛顿/雨果·维文/文斯·沃恩',score:'8.7分',releaseDate:'2016',src:'https://bkimg.cdn.bcebos.com/pic/a08b87d6277f9e2f69c188231630e924b899f321?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U4MA==,g_7,xp_5,yp_5/format,f_auto'},
            {id:3,name:'肖申克的救赎',director:'弗兰克·德拉邦特',performer:'蒂姆·罗宾斯/摩根·弗里曼/鲍勃·冈顿/威廉姆·赛德勒',score:'9.7分',releaseDate:'1994',src:'https://bkimg.cdn.bcebos.com/pic/38dbb6fd5266d016092478b8667ac30735fae6cd9f5b?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UxMTY=,g_7,xp_5,yp_5/format,f_auto'},
            {id:4,name:'当幸福来敲门',director:'加布里尔·穆奇诺',performer:'威尔·史密斯/贾登·史密斯/桑迪·牛顿 ',score:'9.3分',releaseDate:'2006',src:'https://bkimg.cdn.bcebos.com/pic/e1fe9925bc315c6026eed9bd8fb1cb134954776c?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto'}
          ],
          historyPerson:[
            {id:1,name:'蒂姆·罗宾斯',EnglishName:'Tim Robbins',address:'美国,加利福尼亚州,西科维纳',works:'肖申克的救赎、辛普森一家 第十一季、周六夜现场 第一季、政治边缘、忧愁河上桥 第二季',personImg:'https://img1.baidu.com/it/u=401831186,767102162&fm=253&fmt=auto&app=138&f=JPEG?w=270&h=382'}
          ]
      }
  },
  methods: {
      changeMovieChannel(){
          this.a=true
      },
      changePersonChannel(){
          this.a=false
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
};
</script>

<style>
.userHistory {
  display: flex;
  flex-flow: column nowrap;
}
.historyList{
    display: flex;
    width: 100%;
    height: 10%;
}
.showArea{
    width: 100vw;
    height: 90vh;
    display: flex;
    justify-content: center;
    align-items: center;
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
.historyMovie {
  width: 50%;
  height: 5%;
  text-align: center;
  padding: 20rpx 0;
}
.historyPerson {
  width: 50%;
  height: 5%;
  text-align: center;
  padding: 20rpx 0;
}
.active{
  color: var(--themeColor);
  border-bottom: 5rpx solid currentColor;
}


/*  */
.historyMovieShow{
  height: 85vh;
  width: 100vw;
}
.historyPersonShow{
  height: 85vh;
  width: 100vw;
}
ul{
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  flex-flow: column nowrap;
}
.movieShow li{
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-around;
  align-items: flex-start;
  width: 100vw;
  height: 45vh;
  margin: 20rpx;
  margin-bottom: 60rpx;
}
.personShow li{
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-around;
  align-items: flex-start;
  width: 100vw;
  height: 85%;
}
li .watchTime{
  height: 13%;
  width: 100%;
  margin-bottom: 20rpx;
}
li .watchTime span{
  font-size: 52rpx;
  color: gray;
  font-weight: 300;
}
.movie{
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-around;
  align-items: flex-start;
  width: 95vw;
  height: 440rpx;
}
.moviePhoto{
  width: 40%;
  height: 100%;
}
.movieInfo{
  display: flex;
  flex-flow: column nowrap;
  align-items: flex-start;
  justify-content: space-around;
  width: 54%;
  height: 100%;
}
.historyMovieShow img{
  width: 100%;
  height: 100%;
}
.infoItem{
  font-size: 32rpx;
  color: gray;
}

#data{
  height: 35rpx;
  padding: 30rpx 0;
}
#title{
  font-size: 43rpx;
  color: black;
}
#actor{
  overflow:hidden;
  text-overflow:ellipsis;
  display:-webkit-box;
  -webkit-line-clamp:2;
  -webkit-box-orient:vertical
}
.historyPersonShow .personShow{
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  align-items: center;
}
.historyPersonShow .personShow ul{
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-around;
  align-items: center;
}
.historyPersonShow .personShow ul li{
  display: flex;
  justify-content: space-around;
  height: 80%;
  width: 90%;
  border: 3rpx solid grey;
  border-radius: 5%;
  box-shadow: 0 0 10px #CCC;
  padding: 30rpx 15rpx 50rpx;
}
.historyPersonShow .personShow .personImg{
  width: 38%;
  height: 270rpx;
}
.historyPersonShow .personShow .personImg img{
  max-height: 100%;
  max-width: 100%;
  border-radius: 50%;
}
.historyPersonShow .personShow .personInfo{
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-flow: row wrap;
  width: 55%;
  height: 100%;
  color: gray;
  font: normal;
  font-weight: 400;
}
.historyPersonShow .personShow .personInfo span{
  padding: 8rpx;
  font-size: 32rpx;
  font: normal;
  font-weight: 400
}
ul li img{
  width: 100%;
  height: 427rpx
}
</style>