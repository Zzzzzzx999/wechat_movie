<template>
  <div class="mySkin">
        <ul>
            <!-- <li v-for="skin in skins" :key="skin.id">
                <div class="skinImg">
                    <img :src="skin.src" alt=""  :class="{'active':b}" @click="a=skin.id">
                    <div class="skinName">
                        <span>{{skin.name}}</span>
                    </div>
                    <div :class="{'using':b}">
                    </div>
                </div>
             </li> -->
             <li>
                 <div class="skinImg" :class="{'border':a==1}">
                    <img src="https://img2.baidu.com/it/u=1173600065,1739940764&fm=253&fmt=auto&app=138&f=JPEG?w=1180&h=291" mode="aspectFill" alt="" @click="changeToA">
                    <div class="skinName">
                        <span>公路</span>
                    </div>
                    <div :class="{'using':a==1}">
                    </div>
                </div>
             </li>
             <li>
                 <div class="skinImg" :class="{'border':a==2}">
                    <img src="https://i-1-lanrentuku.52tup.com/2020/12/7/99a793d0-9c48-4537-b528-4f1a831e5d75.jpg?imageView2/2/w/1024/" mode="aspectFill" alt="" @click="changeToB">
                    <div class="skinName">
                        <span>黑夜森林</span>
                    </div>
                    <div :class="{'using':a==2}">
                    </div>
                </div>
             </li>
             <li>
                 <div class="skinImg" :class="{'border':a==3}">
                    <img src='https://img0.baidu.com/it/u=1051466376,2052152245&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=332' mode="aspectFill" alt="" @click="changeToC">
                    <div class="skinName">
                        <span>鱼与水</span>
                    </div>
                    <div :class="{'using':a==3}">
                    </div>
                </div>
             </li>
        </ul>
  </div>
</template>

<script>
export default {
    name:'myskin',
    data() {
        return {
            skins:[
                {id:1,name:'公路',src:'https://img2.baidu.com/it/u=1173600065,1739940764&fm=253&fmt=auto&app=138&f=JPEG?w=1180&h=291'},
                {id:2,name:'黑夜森林',src:'https://i-1-lanrentuku.52tup.com/2020/12/7/99a793d0-9c48-4537-b528-4f1a831e5d75.jpg?imageView2/2/w/1024/'},
                {id:3,name:'鱼与水',src:'https://img0.baidu.com/it/u=1051466376,2052152245&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=332'},
            ],
            a:1,
            bgcolor:this.bgcolor
        }
    },
    methods: {
        changeToA(){
            this.a=1
            wx.setBackgroundColor({
                backgroundColor: '#8FBC8F', 
            }),
            wx.setNavigationBarColor({      // 窗口的背景色为白色
                frontColor: '#000000',
                backgroundColor: '#8FBC8F'
            });
            this.backgroundColor = '#8FBC8F'
            this.changeSkin()
        },
        changeToB(){
            this.a=2
            wx.setBackgroundColor({
                backgroundColor: '#855E42', 
            }),
            wx.setNavigationBarColor({      // 窗口的背景色为黑色
                frontColor: '#000000',
                backgroundColor: '#855E42'
            });
            this.backgroundColor = '#855E42'
            this.changeSkin()
        },
        changeToC(){
            this.a=3
            wx.setBackgroundColor({
                backgroundColor: '#0000FF', 
            }),
            wx.setNavigationBarColor({      // 窗口的背景色为蓝色
                frontColor: '#000000',
                backgroundColor: '#0000FF',
            });
            this.backgroundColor = '#0000FF'
            this.changeSkin()
        },
        changeSkin(){
            let background = {
                color: this.backgroundColor,
                A:this.a
            }
            wx.setStorageSync('background',background)
        }
    },
   /*  mounted(){
        setTimeout(() => {
          let background = {
                bgc: this.backgroundColor
            }
           wx.setStorageSync('color',background)  
        }, 3000);
        
    } */
    onShow(){
        if (wx.getStorageSync('background')) {
            this.background = wx.getStorageSync('background')
            this.bgcolor=this.background.color
            this.a=this.background.A
        }
        wx.setNavigationBarColor({      // 窗口的背景色
            frontColor: '#000000',
            backgroundColor: this.bgcolor
        });
        wx.setBackgroundColor({
            backgroundColor: this.bgcolor, // 窗口的背景色为白色
        })
    }
}
</script>

<style>
.mySkin ul{
    display: flex;
    align-items: center;
    flex-direction: row;
    justify-content: center;
    flex-wrap: wrap;
    width: 100vw;
}
ul li{
    width: 95%;
    height: 350rpx;
    background-color: white;
    margin: 28rpx 0;
    border: 1px solid #DDDDDD;
    border-radius: 15rpx;
}
.skinImg{
    position: relative;
    width: 100%;
    height: 100%;
}
.border{
    /* border: 10rpx solid greenyellow; */
}
.skinName{
    display: flex;
    align-items: center;
    width: 100%;
    position: absolute;
    bottom: 0;
    left: 0;
    height: 80rpx;
    width: 100%;
    background-color: rgb(56, 54, 54);
    opacity: 0.7;
}
li .skinImg img{
    width: 100%;
    height: 100%;
    border-radius: 5%;
}
li .skinImg .using{
    position: absolute;
    top: 0;
    right: 0;
    width: 30rpx;
    height: 30rpx;
    background-color: greenyellow;
}
li .skinImg .using::before {
    content: "";
    width:0;
    height: 0;
    border:60px solid transparent;
    border-right:60px solid greenyellow;
    transform: rotate(135deg);
    position: absolute;
    right: -61px;
    top: -61px;
    cursor: pointer;
}
li .skinImg .using::after {
	content: "在用";
	width: 40px;
	height: 30px;
	color: #FFF;
	transform: rotate(45deg);
	position: absolute;
	right: 13px;
	top: 16px;
	font-weight: bold;
	letter-spacing:2px;
	cursor: pointer;
}
li .skinName span{
    color: aliceblue;
    margin-left: 30rpx;
}

/* .active{
    border: 6rpx solid greenyellow;
} */
</style>