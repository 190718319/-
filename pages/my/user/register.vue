<template>
	<view id="login">
		<view class="lvyou_logo">
			<image class="logo" src="../../../static/image/lvyou.png"></image>
		</view>
		<view class="webcome">
			创建一个新账户
		</view>
		<input type="text" v-model="username" placeholder="请输入用户名" confirm-type="next"/>
		<input type="password" v-model="password" placeholder="请输入密码"  confirm-type="next"/>
		<input type="password" v-model="password2" placeholder="请再次输入密码"  confirm-type="done"/>
		<button type="default" @click="register">注册</button>
		<navigator class="login" url="login">已经有账户了?点此登录</navigator>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				username:'',
				password:'',
				password2:'',
			}
		},
		methods:{
			register(){
				if(this.username && this.password && this.password2){
					if(this.password == this.password2){
						console.log(11)
						uni.request({
						    url: 'https://wxt.show/register',
						    method: 'POST',
						    data: {username:this.username,password:this.password},
						    header:{
								'Content-Type': 'application/json'
							},
							success: res => {
								if(res.data.code == 200){
									uni.navigateTo({
										url:"./login"
									})
								}
								uni.showToast({
								    title: res.data.msg,
									icon:"none",
								    duration: 2000
								});
						    },
						    fail: () => {},
						    complete: () => {}
						});
					}else{
						uni.showToast({
						    title: '密码不一致',
							icon:"none",
						    duration: 2000
						});
					}
				}else{
					uni.showToast({
					    title: '请输入完整信息',
						icon:"none",
					    duration: 2000
					});
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	#login{
		background-color: #f0f3f4;
		text-align: center;
		position: fixed;
		top: 40px;
		bottom: 0;
		left: 0;
		right: 0;
		.lvyou_logo{
			width: 100%;
			text-align: center;
			.logo{
				width: 360rpx;
				height: 280rpx;
				margin: 30px auto;
			}
		}
		.webcome{
			font-size: 16px;
			font-weight: bold;
		}
		input{
			border: 1px solid #CCCCCC;
			background-color: #fff;
			height: 40px;
			margin: 20px auto 0;
			width: 80%;
		}
		button{
			border: 1px solid #7266ba;
			background-color: #7266ba;
			height: 40px;
			margin: 30px auto 0;
			width: 80%;
			font-size: 16px;
			color: #FFFFFF;
		}
		.login{
			font-size: 14px;
			margin-top: 10px;
			color: #337ab7;
		}
	}
</style>
