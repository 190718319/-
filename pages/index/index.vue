<template>
	<view class="content">
		<!--搜索框-->
		<view class="input">
			<input class="weui-input" disabled placeholder-style="color:#a0a0a0" placeholder="搜索目的地" @click="goSearch" />
			<image class="icon_search" src="../../static/image/search.png"></image>
		</view>
		<!--搜索框 end-->
		<!-- 轮播图 -->
		<view class="banner">
			<swiper :indicator-dots="true" circular="true" :autoplay="true" :interval="2000" :duration="500" previous-margin="24px"
			 next-margin="24px" :style="'height:'+swiperHeight+'px;'">
				<swiper-item>
					<view style="padding: 0 16rpx;">
						<image src="../../static/image/banner01.jpeg" mode="widthFix" @load="imgH"></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view style="padding: 0 16rpx;">
						<image src="../../static/image/banner02.jpeg" mode="widthFix"></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view style="padding: 0 20rpx;">
						<image src="../../static/image/banner01.jpeg" mode="widthFix"></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view style="padding: 0 20rpx;">
						<image src="../../static/image/banner02.jpeg" mode="widthFix"></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<!-- 轮播图 end-->
		<!-- 导航栏 -->
		<view class="girdNav">
			<view class="li" v-for="(item,index) in girdList" :key="index">
				<navigator :url="item.url">
					<image :src="item.icon" ></image>
					<view class="text">{{item.text}}</view>
				</navigator>
			</view>
		</view>
		<!-- 导航栏 end-->
		<!-- 热门问答 -->
		<view style="text-align:center">热门问答</view>
		<qa-list></qa-list>
		<!-- 热门问答 -->
		<!-- 热门攻略 -->
		<view style="text-align:center">精选功略</view>
		<guide-list></guide-list>
		<!-- 热门攻略 -->
		
		<view class="">
			<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem"></uni-segmented-control>
			<view class="content">
				<view v-show="current === 0">
					<scenic-list></scenic-list>
				</view>
				<view v-show="current === 1">
					<goods-list></goods-list>
				</view>
			</view>
		</view>
		<!-- 景区推荐 -->
		
	</view>
</template>

<script>
	import detail from '../../static/js/detail.js';
	import guideList from '../../components/public/guideList.vue';
	import qaList from '../../components/public/QAList.vue';
	import goodsList from '../../components/public/goodsList.vue';
	import scenicList from '../../components/public/scenicList.vue';
	export default {
		components:{
			guideList,
			qaList,
			goodsList,
			scenicList
		},
		data() {
			return {
				swiperHeight: 150,
				items: ['景区推荐','周边好物'],
				current: 0,   //分段器默认选中
				girdList:[
					{
						icon:"../../static/image2/icon-qinzi.png",
						text:"文本"
					},{
						icon:"../../static/image2/icon-qinzi.png",
						text:"文本"
					},{
						icon:"../../static/image2/icon-qinzi.png",
						text:"文本"
					},{
						icon:"../../static/image2/icon-qinzi.png",
						text:"文本"
					},{
						icon:"../../static/image2/icon-qinzi.png",
						text:"文本"
					},{
						icon:"../../static/image2/icon-qinzi.png",
						text:"旅游资讯",
						url:"./girdNav/news"
					}
				],
				}
			},
			methods: {
				//轮播图高度自适应
				imgH(e) {
					console.log(e.detail.height)
					var winWid = uni.getSystemInfoSync().windowWidth;
					this.swiperHeight = e.detail.height / e.detail.width * (winWid - 60)
				},
				goSearch() {
					uni.navigateTo({
						url: "../search/search"
					})
				},
				goDetail(e){
					uni.navigateTo({
					    url: '../jingdianDetail/jingdianDetail?sid='+e.currentTarget.dataset.sid
					});
				},
				//切换分段器
				onClickItem(e) {
					if (this.current !== e.currentIndex) {
						this.current = e.currentIndex;
					}
				}
			},
			onLoad() {
				console.log(detail.length)
			},
		}
</script>

<style lang="scss">
	.girdNav{
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-around;
		.li{
			width: 30%;
			font-size: 30rpx;
			text-align: center;
			image{
				width: 120rpx;
				height: 120rpx;
			}
		}
	}
	.content {
		background-color: rgb(249, 249, 249);
	}

	.input {
		background-color: #f9f9f9;
		height: 30px;
		padding: 5px 20px;
		position: relative;
	}

	.weui-input {
		background-color: #fff;
		border-radius: 15px;
		height: 30px;
		line-height: 30px;
		padding-left: 30px;
		font-size: 14px;

	}

	.input .icon_search {
		position: absolute;
		left: 28px;
		top: 12px;
		width: 16px;
		height: 16px;
	}

	.banner {
		margin-top: 10px;

		image {
			width: 100%;
			border-radius: 20rpx;
		}
	}
	
	
	
</style>
