<template>
    <div class="myGollery">
        <div class="historyGollery">
            <!-- <ul>
                <li v-for="g in imgList" :key="g.id">
                    <img :src="g.img" alt="">
                </li>
            </ul> -->
            <img v-for="g in imgList" :key="g.id" :src="g.img" alt="" mode="aspectFill">
        </div>
        <div class="uploadGollery">
            <button>上传</button>
        </div>
    </div>
</template>

<script>
export default {
    name:'gallery',
    data() {
        return {
            imgList:[
                {id: 1,img:"https://bkimg.cdn.bcebos.com/pic/eaf81a4c510fd9f9d72a89c86966c32a2834349b0e74?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg"},
                {id: 2,img:"https://img0.baidu.com/it/u=3158986335,2577920955&fm=253&fmt=auto&app=120&f=JPEG?w=500&h=750"},
                {id: 3,img:"https://bkimg.cdn.bcebos.com/pic/ca1349540923dd54564ebf768d5ba4de9c82d158e229?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg"},
                {id: 4,img:"https://bkimg.cdn.bcebos.com/pic/14ce36d3d539b6003af3e7698c01222ac65c113819e9?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2UyNzI=,g_7,xp_5,yp_5/format,f_auto"},
                {id: 5,img:"https://bkimg.cdn.bcebos.com/pic/0df3d7ca7bcb0a46f21fefd7b228e1246b600d330183?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto"},
            ]
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
/* ul{
    display: flex;
    justify-content: flex-start;
}
li{
    width: 33%;
    padding: 0;
    height: auto;
}
img{
    width: 300rpx;
    height: 300rpx;
} */
.historyGollery{
    display: flex;
    justify-content: flex-start;
    flex-flow: row wrap;
}
img{
    width: 33%;
    height: 105.6px;
}


.uploadGollery{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 150rpx;
}
button{
    text-align: center;
    padding: 0 60rpx !important;
    color: forestgreen;
    font-size: 15px;
    margin: 0;
}
button::after{
    border: 3px solid forestgreen;
}
</style>