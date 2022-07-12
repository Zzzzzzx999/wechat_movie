<template>
    <div class="location">
        <map name="" v-bind:longitude="marks[0].longitude" :latitude="marks[0].latitude" 
            scale="15" v-bind:markers="marks"></map>
        <div class="showLocation">
            <div class="name">
               <span>你的当前位置在: {{marks[0].name}}</span>
            </div> 
            <div class="detail">
               <span>gps坐标:经度({{marks[0].longitude}}),纬度({{marks[0].latitude}})</span>
            </div> 
        </div>
        <button @click="chooseLocation">选择位置</button>
        <button @click="update">自动更新所在位置</button>
    </div>
</template>

<script>
export default {
    name:'location',
    data() {
        return {
            marks:[{
                id:1,
                latitude:24.479099,
                longitude:118.090000,
                name:"厦门工学院",
                iconPath:'../static/icons/定位.png',
                width:30,
                height:30
            }]
        }
    },
    methods: {
        chooseLocation(){
            wx.chooseLocation({
                success: (result) => {
                    console.log(result);
                    this.marks[0].latitude=result.latitude
                    this.marks[0].longitude=result.longitude
                    this.marks[0].name=result.name
                },
                fail: () => {},
                complete: () => {}
            });
        },
        update(){
            wx.getLocation({
                type: 'wgs84',
                isHighAccuracy:true,
                altitude: false,
                success: (result)=>{
                    console.log(result);
                    this.marks[0].latitude=result.latitude
                    this.marks[0].longitude=result.longitude
                    this.marks[0].name='未知位置'
                },
                fail: ()=>{},
                complete: ()=>{}
            });
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
    },
}
</script>

<style>
map{
    width:100%;
    height:800rpx
}
.name{
    text-align: center;
    margin: 20rpx;
}
.detail{
    text-align: center;
    color: gainsboro;
    font-size: 30rpx;
    margin:20rpx;
}
button{
    background-color: #8FBC8F;
    width: 600rpx;
    margin-top: 20rpx;
}
</style>