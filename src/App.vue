<script>
	export default {
        data() {
            return {
                bgcolor:'#8FBC8F'
            }
        },
		onLaunch: function() {
			console.log('App Launch')
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
		},
		onHide: function() {
			console.log('App Hide')
		},
        mounted() {
            console.log(1111111);
            console.log(this.bgcolor);
            if (wx.getStorageSync('background')) {
                this.background = wx.getStorageSync('background')
                this.bgcolor=this.background.color
            }
            wx.setNavigationBarColor({      // 窗口的背景色
                frontColor: '#000000',
                backgroundColor: this.bgcolor
            });
        },
	}
</script>

<style>
	/*每个页面公共css */
    body{
        background-color: whitesmoke;
    }
	ul{
        display: flex;
        align-items:center;
        flex-direction: row;
        justify-content: space-around;
        flex-wrap: wrap;
        width: 100vw;
    }
    ul li{
        width: 100%;
        height: 490rpx;
        margin: 20rpx 0;
        border-radius: 15rpx;
    }
    ul li span{
        padding: 15rpx;
        font-size: 32rpx;
        font-family: Arial, Helvetica, sans-serif;
        font: bolder;
        font-weight: 600;
    }
    ul li img{
        width: 100%;
        height: 470rpx;
    }
    li button{
        margin-right: 14rpx;
        padding: 0 10rpx !important;
        color: gray;
    }
    .filmTypes{
        padding: 15rpx 20rpx;
    }
	/* button::after{
		padding: 0 10rpx;
	} */

    /* 评分栏 */
    .photo{
        position: relative;
    }
    .filmScore{
        display: flex;
        position: absolute;
        justify-content: flex-end;
        align-items: center;
        bottom: 0%;
        right: 0%;
        transform: translate(0px, -5px);
        width: 340rpx;
        height: 61rpx;
        color: whitesmoke;
        background-color: #444444;
        z-index: 999;
        opacity: 0.7;
        font-size: 35rpx;
    }
    .filmScore span{
        font-size: 32rpx;
        font-weight: 200;
        color: white;
    }
    /* 电影类型盒子 */
    #types{
        background-color: #f8f8f8;
        border-radius: 5px;
        border: 3rpx solid rgb(221, 219, 219);
        box-sizing: border-box;
        cursor: pointer;
        display: inline-block;
        display: inline-block;
        font-size: 30rpx;
        line-height: 2.3;
        margin-right: 14rpx;
        padding: 0 10rpx;
        color: gray;
        overflow: hidden;
        position: relative;
        text-align: center;
        text-decoration: none;
    }

    /* 原本自己写的的导航栏样式 */
    /* .pageFooter{
        display: flex;
		justify-content: center;
        height: 40px;
        width: 100vw;
        position: fixed;
        bottom: 0%;
        z-index: 999;
        background-color: whitesmoke;
    }
    .bannerItem{
		display: flex;
		position: relative;
        height: 50rpx;
        width: 25%;
		padding: 0 50rpx;
    }
    .bannerItem img{
		display: flex;
        justify-content: space-around;
        width: 100%;
        height: 100%;
		max-width: 90rpx;
		max-height: 90rpx;
    }
    .bannerItem span{
        display: flex;
        justify-content: space-around;
        align-items: center;
        font-size: 32rpx;
    } */
</style>
