<template>
	<view class="content">
		<div class="registerHeader">
			<image class="logo" src="/static/logo.png"></image>
			<text class="title">{{title}}</text>
		</div>
		<div class="registerContent">
			<div class="userInfoAccount">
				<span>账号:</span>
				<input type="text" id="demo" v-model.trim="userInfo.account">
			</div>
			<div class="userInfoPassword">
				<span>密码: </span>
				<input type="password" v-model="userInfo.password">
			</div>
			<!-- ⟪用户协议⟫ -->
			<!-- <checkbox value="accept">阅读并接受 <a href="www.baidu.com/">⟪用户协议⟫</a> </checkbox> -->
			<!-- 这边结构层有父子层级，checkbox是小程序的组件，这个组件应该被渲染成块级元素，这边checkbox元素内的未定义元素标签的文字应该是被定义为块级元素了，如果你想要里面的内容在一行，可以对父元素使用flex布局，或对a标签进行float浮动，建议flex。蒙圈了，这个应该是这个组件做了什么处理了，改一下布局 -->
			<div class="userAccept">
				<checkbox value="accept">阅读并接受</checkbox>
				<a href="www.baidu.com/">⟪用户协议⟫</a>
			</div>
			<button @click="btnPath()">登录</button>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'ZZX MOVIES',
				userInfo:{
					account:'',
					password:'',
					agree:'',
				}
			}
		},
		onLoad() {

		},
		methods: {
			btnPath() {
				// console.log(123)
				// uni.navigateTo({url: '/pages/popular'})
				wx.switchTab({url:'/pages/popular'})
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
		},
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		font-size: 36rpx;
	}

	input{
		display: flex;
		border: 1px solid #2aabd2;     
  		border-radius: 3px;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin: 200rpx auto 50rpx auto;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}


	/*  */
	.registerHeader{
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		font-size: 36rpx;
		margin-bottom: 50rpx;
	}
	.logo{
		height: 200rpx;
		width: 200rpx;
		margin: 100rpx auto 50rpx auto;
	}
	
	.userInfoAccount {
		display: flex;
		flex-flow: row nowrap;
		align-items: center;
		justify-content: center;
		font-size: 36rpx;
		margin: 60rpx 0;
	}
	.userInfoPassword {
		display: flex;
		flex-flow: row nowrap;
		align-items: center;
		justify-content: center;
		font-size: 36rpx;
		margin: 60rpx 0 200rpx 0;
	}

	.registerContent checkbox{
		font-size: 30rpx;
		margin: 30rpx 0;
	}
	.userAccept{
		display: flex;
		align-items: center;
	}
</style>
