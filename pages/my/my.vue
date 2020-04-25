<template>
	<view class="my">
		<!-- #ifdef H5 || APP-PLUS-->
			<view class="personal_info">
			    <view class="photo_wrap" >
			        <image src="../../static/image/unLogin.png"></image>
			    </view>
			    <view class="nickname" v-if="username">
			        当前用户: {{username}}
			    </view>
			    <button @click="login_H5" v-if="!username">登录/注册</button>
			</view>
		<!-- #endif -->
		
		<!-- #ifdef MP-WEIXIN -->
			<view class="personal_info">
			    <view class="photo_wrap">
			        <image :src="userInfo.tx_url"></image>
			    </view>
			    <view class="nickname" v-if="userInfo">
			        {{userInfo.username}}
			    </view>
				<view class="">
					<button open-type="getUserInfo" v-if="!userInfo" @getuserinfo="bindGetUserInfo">授权登录</button>
					<button v-if="!isSync&&userInfo" @click="syncUser">同步网页端数据</button>
				</view>
			</view>
		<!-- #endif -->
		<view class="ul">
			<navigator url="collection/collection">
		        <view class="li">
		            我的收藏
		            <image src="../../static/image2/icon-arrow.png"></image>
		        </view>
			</navigator>
			<navigator url="order/order">
		        <view class="li">
		            我的订单
		            <image src="../../static/image2/icon-arrow.png"></image>
		        </view>
		    </navigator>
			<view class="li">
				我的地址
				<image src="../../static/image2/icon-arrow.png"></image>
			</view>
		    <view class="li">
		        设置
		        <image src="../../static/image2/icon-arrow.png"></image>
		    </view>
			<view class="li" @click="back">
				退出登录
				<image src="../../static/image2/icon-arrow.png"></image>
			</view>
		</view>
	</view>
</template>
	
<script>
	export default{
		data(){
			return{
				userInfo: null,  //微信信息
				username:'',    //h5信息
				isSync:false
			}
		},
		methods:{
			bindGetUserInfo(e) {
				let _this = this;
				uni.login({
					provider: 'weixin',
					success(res){
						// console.log(res.code);
						if(res.code){
							let wxcode = res.code;
							//获取用户信息
							uni.getUserInfo({
								provider: 'weixin',
								success:function(res){
									_this.userInfo = res.userInfo;
									uni.request({
										url:"https://wxt.show/loginwx",   //携带code
										method: 'POST',
										header:{
											'Content-Type': 'application/json'
										},	
										data: {
											wxcode,
											tx_url:res.userInfo.avatarUrl,
											username:res.userInfo.nickName
										},
										success: (res) => {
											// const userID = res.data.userID
											console.log(res)
											uni.setStorage({
											    key: 'user',
											    data: {username:res.data.username,tx_url:res.data.tx_url},
											    success: function () {
													uni.showToast({
													    title: res.data.msg,
														icon:"none",
													    duration: 2000
													});
											    }
											});
										},
										fail() {
											console.log("请求失败")
										}
									})
								}
							})
						}else{
							console.log("登录失败")
						}
					}
				})
			},
			syncUser(){
				let _this = this;
				uni.getStorage({
					key: 'user',
					success: function (res) {
						_this.isSync=true
					}
				});
			},
			login_H5(){
				uni.navigateTo({
					url:"./user/login"
				})
			},
			back(){
				let _this = this;
				uni.getStorage({
					key: 'user',
					success: function (res) {
						if(res){
							uni.showModal({
							    title: '提示',
							    content: '是否退出登录',
							    success: function (res) {
							        if (res.confirm) {
							            uni.removeStorage({
							                key: 'user',
							                success: function (res) {
												// #ifdef H5
												_this.username='';
												// #endif
												// #ifdef MP-WEIXIN
												_this.userInfo=null;
												_this.isSync=false
												// #endif 
							                    uni.showToast({
							                        title: '你已经退出登录',
							                        duration: 1500
							                    });
							                }
							            });
							        }
							    }
							});
						}else{
							uni.showToast({
							    title: '尚未登录',
							    duration: 1500
							})
						}
					}
				});
				
			}
		},
		/**
		 * 生命周期函数--监听页面加载
		 * 
		 */
		onShow: function(){
			let _this = this;
			// #ifdef H5 
				uni.getStorage({
					key: 'user',
					success: function (res) {
						if(res){
							_this.username = res.data.username;
						}
					}
				});
			// #endif 
		},
		/**
		 * 生命周期函数--监听页面加载
		 */
		onLoad: function (options) {
			let _this = this;
			// #ifdef MP-WEIXIN
				uni.getStorage({
					key: 'user',
					success: function (res) {
						if(res){
							_this.userInfo = {
								username:res.data.username,
								tx_url:res.data.tx_url
							}
						}
					}
				});
			//https://api.weixin.qq.com/sns/jscode2session?appid=wx6d3723ce726a5ab3&secret=0cf1b50462e7b4db239861be290b0bc3&js_code=033x6Ifd1M4AKw0k0sed1ABmfd1x6Ifg&grant_type=authorization_code
			//https://api.weixin.qq.com/sns/jscode2session?appid=APPID&secret=SECRET&js_code=JSCODE&grant_type=authorization_code
			// #endif
		},
		
	}
</script>

<style>
	/* pages/my/my.wxss */
	.personal_info{
		background: url('https://static.qyer.com/images/user2/index/headImage_lite.png?v=') no-repeat;
		background-size: cover;
		
	}
	.personal_info{
	    padding:20px 0px;
	    background-color: #fff;
	}
	.photo_wrap {
	    text-align: center;
		height: 95px;
	}
	.photo_wrap image{
	    width:90px;
	    height: 90px;
	    border-radius: 50%;
	}
	.nickname{
	    text-align: center;
	    color:#fff;
	}
	button{
	    margin-top: 10px;
	}
	.ul{
	    font-size: 14px;
	    border-top: 1px solid #e5e5e5;
	}
	.li{
	    padding:0 10px;
	    height: 45px;
	    line-height: 45px;
	    border-bottom: 1px solid #e5e5e5;
	    position: relative;
	}
	.li image{
	    width: 20px;
	    height: 20px;
	    position: absolute;
	    top:12px;
	    right: 10px;
	}
</style>
