<template>
	<view class="">
		<!-- 周边商城 -->
		<view class="goodsList">
			<view class="li" v-for="(item,index) in goodsList" :key="index">
				<navigator url="/pages/shopDetail/shopDetail">
					<image mode="widthFix" :src="item.image" style="width:100%;display:block;"></image>
					<view class="info">
						<view class="title">
							{{item.name}}
						</view>
						<text>￥{{item.price}}</text>
						<image class="icon_cart" src="../../static/image2/cart.png"></image>
					</view>
				</navigator>
			</view>
			<view class="lookmore">查看更多</view>
		</view>
		<!-- 周边商城 end-->
	</view>
</template>

<script>
	export default{
		data(){
			return {
				goodsList: [{
						id: 1,
						name: "花芽原创仲夏夜之梦系列双层项链女款简约气质锁骨链纯银吊坠礼物",
						price: '28',
						image: "../../static/image2/goodslist01.jpg",
						imgs: [
							"../../static/image2/loop01.jpg",
							"../../static/image2/loop02.jpg",
							"../../static/image2/loop03.jpg",
							"../../static/image2/loop04.jpg"
						],
						categroyId: 0,
						isStar: false
					},
					{
						id: 2,
						name: "花芽原创设计美人鱼耳夹女纯银日韩学生长款流苏无耳洞耳骨夹耳饰",
						price: '28',
						image: "../../static/image2/goodslist02.jpg",
						imgs: [
							"../../static/image2/loop01.jpg",
							"../../static/image2/loop02.jpg",
							"../../static/image2/loop03.jpg",
							"../../static/image2/loop04.jpg"
						],
						categroyId: 1,
						isStar: false
					},
					{
						id: 3,
						name: "花芽s925纯银不对称耳钉个性迷你小耳骨钉气质简约耳饰潮",
						price: '28',
						image: "../../static/image2/goodslist03.jpg",
						imgs: [
							"../../static/image2/loop01.jpg",
							"../../static/image2/loop02.jpg",
							"../../static/image2/loop03.jpg",
							"../../static/image2/loop04.jpg"
						],
						categroyId: 2,
						isStar: false
					},
					{
						id: 4,
						name: "花芽原创樱花戒指情侣一对纯银简约潮人个性学生百搭对戒",
						price: '28',
						image: "../../static/image2/goodslist04.jpg",
						imgs: [
							"../../static/image2/loop01.jpg",
							"../../static/image2/loop02.jpg",
							"../../static/image2/loop03.jpg",
							"../../static/image2/loop04.jpg"
						],
						categroyId: 3,
						isStar: false
					},
					{
						id: 5,
						name: "花芽s925纯银不对称耳钉个性迷你小耳骨钉气质简约耳饰潮",
						price: '28',
						image: "../../static/image2/goodslist05.jpg",
						imgs: [
							"../../static/image2/loop01.jpg",
							"../../static/image2/loop02.jpg",
							"../../static/image2/loop03.jpg",
							"../../static/image2/loop04.jpg"
						],
						categroyId: 4,
						isStar: false
					},
					{
						id: 6,
						name: "花芽s925纯银不对称耳钉个性迷你小耳骨钉气质简约耳饰潮",
						price: '28',
						image: "../../static/image2/goodslist06.jpg",
						imgs: [
							"../../static/image2/loop01.jpg",
							"../../static/image2/loop02.jpg",
							"../../static/image2/loop03.jpg",
							"../../static/image2/loop04.jpg"
						],
						categroyId: 5,
						isStar: false,
					}
				],
			}
		}
	}
</script>

<style>
	.goodsList{
		background-color: rgb(249, 249, 249);
		padding: 10px 6px;
	}
	.goodsList::after{
		content: '';
		display: block;
		clear: both;
	}
	.goodsList .li{
		width: 46%;
		margin: 0 2% 2%;
		float: left;
	}
	.goodsList .info{
		padding: 8px;
		background-color: #fff;
	}
	.goodsList .li .title{
		margin-bottom: 10px;
		font-size: 14px;
		color: #666;
		/* height: 40px; */
		overflow: hidden;
		display: -webkit-box;
		text-overflow: ellipsis;
		word-break: break-all;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
	}
	.goodsList .li text{
		color: rgb(254,94,21)
	}
	.goodsList .li .icon_cart{
		width: 18px;
		height: 18px;
		float: right;
	}
	.lookmore{
		width: 96%;
		text-align: center;
		color: #999;
		background-color: #fff;
		height: 40px;
		line-height: 40px;
		margin: 20px auto;
		overflow: hidden;
		border: 1px solid #ccc;
	}
</style>
