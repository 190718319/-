<template>
	<view id="jingdianDetail">
		<view class="scenicDetail" 
			v-for="(item, index) in dataDetailList" 
			:key="item.title+index">
			<view class="title">{{item.title}}</view>
			<image :src="item.img" mode="widthFix" style="width: 100%;"></image>
			<view class="referral">{{item.referral}}</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				dataDetailList:[]
			}
		},
		onLoad:function(e){
			console.log(e.sid)
		    uni.request({
		        url: 'https://wxt.show/jingdianDetail/'+ e.sid,
		        method: 'GET',
		        data: {},
		        success: res => {
		            this.dataDetailList = res.data.data.result;
		        },
		        fail: () => {},
		        complete: () => {}
		    });
		}
	}
</script>

<style lang="scss">
	#jingdianDetail{
		padding: 0 30rpx;
		image{
			border-radius: 10rpx;
		}
		.title{
			font-size: 16px;
			font-weight: bold;
		}
		.referral{
			font-size: 16px;
			text-indent: 32px;
			margin-bottom: 20rpx;
		}
	}
</style>
