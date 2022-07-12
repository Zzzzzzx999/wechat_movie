<template>
    <div class="searchPage">
        <div class="search">
            <div class="searchBox">
                <!-- <button size="mini">默认</button> -->
                <div class="box"><span>默认</span></div>
                <input type="text" placeholder="请输入电影标题、演员或导演" v-model.trim="keyWord" @confirm="getConfirmKeyWord">
                <!-- <button size="mini" @click="getConfirmKeyWord1">搜索</button> -->
                <div class="box" @click="getConfirmKeyWord1"><span>搜索</span></div>
            </div>
        </div>
        <div class="popularSearch">
            <span><img src="../static/icons/主题.png" alt="">热门搜索</span>
            <div class="searchList">
                <div id="types" v-for="(item,index) in popularSearchList" :key="index" @click="changeValue" :data-keyword="item"><span>{{item}}</span></div>
                <!-- <button size="mini" v-for="(item,index) in popularSearchList" :key="index" @click="changeValue" :data-keyword="item">{{item}}</button> -->
            </div>
        </div>
        <div class="popularLable">
            <span><img src="../static/icons/主题.png" alt="">热门标签</span>
            <div class="lableList">
                <div id="types" v-for="(item,index) in popularLableList" :key="index" @click="changeValue" :data-keyword="item"><span>{{item}}</span></div>
                <!-- <button size="mini" v-for="(item,index) in popularLableList" :key="index" @click="changeValue" :data-keyword="item">{{item}}</button> -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'name',
    data() {
        return {
            keyWord:'',
            popularSearchList:['悬崖之上','千与千寻','肖申克的救赎','摆渡人','我不是潘金莲',
            '驴得水','这个杀手不太冷','海贼王之黄金城','西游伏妖片','我在故宫修文物','你的名字'],
            popularLableList:['动作','喜剧','爱情','悬疑'],
            allList:[]
            // List:['功夫熊猫']
        }
    },
    methods: {
        /* popularFilms(popularFilms){
            console.log('@@@',popularFilms);
        }, */
        getConfirmKeyWord(event){
            this.keyWord = event.detail.value
            uni.navigateTo({url: '../pages/searchResult?keyWord=' + this.keyWord})
            this.keyWord =''
            console.log('@@@',event);
        },  
        getConfirmKeyWord1(){
            uni.navigateTo({url: '../pages/searchResult?keyWord=' + this.keyWord})
            this.keyWord =''
        },
        changeValue(event){
            this.keyWord = event.target.dataset.keyword
            uni.navigateTo({url: '../pages/searchResult?keyWord=' + this.keyWord})
            this.keyWord =''
            console.log('@',event);
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
    /* mounted() {
        this.$bus.$on('popularFilms',(popularFilms)=>{
            console.log('@@@',popularFilms);
        })
    }, */
}
</script>

<style>
.search{
    display: flex;
    flex-flow: row nowrap;
    align-items: center;
    justify-content: center;
    position: relative;
    margin-top: 50rpx;
    width: 100%;
    height: 150rpx;
}
.search .box{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 70rpx;
    width: 110rpx;
    border: 1rpx solid gray;
}
.searchPage #types{
    background-color: #f8f8f8;
    border-radius: 5px;
    border: 3rpx solid rgb(221, 219, 219);
    box-sizing: border-box;
    color: #000;
    cursor: pointer;
    display: inline-block;
    font-size: 30rpx;
    line-height: 2.2;
    padding: 0 24rpx;
    margin: 5rpx 12rpx;
    overflow: hidden;
    position: relative;
    text-align: center;
    text-decoration: none;
}
.searchBox{
    display: flex;
    flex-flow: row nowrap;
    align-items: center;
    justify-content: center;
    position: relative;
    border: 1px solid grey;
    width: 700rpx;
    height: 70rpx;
    /* border-radius: 10rpx; */
    font-size: 32rpx;
    font-weight: 500;
}
input{
    border-radius: 6px;
    flex-grow: 1;
    padding-left: 25rpx;
}

.popularSearch{
    margin: 100rpx 50rpx;
}
img{
    max-width: 35rpx;
    max-height: 35rpx;
}
.searchList{
    margin: 30rpx 0;
}
.popularLable{
    margin: 100rpx 50rpx;
}
.lableList{
    margin: 30rpx 0;
}
span{
    font: bolder;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.search button{
    padding: 0 30rpx !important;
    margin: 0 !important;
}
button{
    padding: 0 30rpx !important;
    margin: 0 10rpx;
}
</style>