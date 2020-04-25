<template>
	<view class="shopDetail">
		<!-- 轮播图 -->
		<view>
		    <swiper indicator-dots="true" indicator-color="red" autoplay="true" interval="3000" duration="500" :style="'height:'+swiperHeight+'px;'">
		        <block v-for="(item,index) in goods[0].goodsImgs" :key="index">
		            <swiper-item>
		                <view>
		                    <image class="loop_img" mode="widthFix" :src="item" style="width:100%" @load='imgH'></image>
		                </view>
		            </swiper-item>
		        </block>
		    </swiper>
		</view>
		<!-- 轮播图 end-->
		<!-- 商品详情 -->
		<view class="goods_info_top">
		    <view class="goods_title">
		        {{goods[0].goodsName}}
		        <view class="goods_collect_btn" >
		            <block v-if="!isStar" >
		                <image src="../../static/image2/icon-aixin1.png" @bindtap="star"></image>
		                <text>未收藏</text>
		            </block>
		            <block v-if="isStar" >
		                <image src="../../static/image2/icon-aixin.png" @bindtap="star"></image>
		                <text>已收藏</text>
		            </block>
		        </view>
		    </view>
		    <view class="goods_price">
		        <text>￥{{goods[0].goodsPrice}}</text>
		        <text class="goods_old_price">￥{{goods[0].goodsPriceOld}}</text>
		    </view>
		</view>
		<!-- 商品详情 end-->
		<view class="content">
		    <view class="title">商品详情</view>
		    <image mode="widthFix"
		        :src="goods[0].goodsImage"         
		        style="width:96%;margin:0 auto;display:block">
		    </image>
		    <image mode="widthFix" v-for="(item,index) in detailsList" :key="index"
		        :src="item"         
		        style="width:100%">
		    </image>
		    
		</view>
		<!-- 商品详情 end-->
		
		<!-- 底部 -->
		<view class="goods_bottom_btn">
		    <view>
		        <view class="btn dv1">
		            <view class="box">
		                <image src="../../static/image2/car.png" @bindtap="getCart"></image>
		                <text class="goods_num">{{num}}</text>
		            </view>
		        </view>
		        <view class="btn dv2" bindtap="getIndex">
		            首页
		        </view>
				<navigator url="pay/pay">
					<view class="btn dv4">
						前往付款
					</view>
				</navigator>
		        
		    </view>
		</view>
	</view>
</template>

<script>
	export default{
		data:function(){
			return {
				swiperHeight: 170,
				isStar: false,  //是否收藏
				goods: [
					{
						id: 3,
						goodsName: '商品名称123123123213132,商品名称123123123213132',
						goodsImage: "../../static/image2/goods01.jpg",
						goodsImgs: [
							"../../static/image2/loop01.jpg",
							"../../static/image2/loop02.jpg",
							"../../static/image2/loop03.jpg"
						],
						goodsPrice: "210.00",
						goodsPriceOld: "300.00",
						goodsDetail: "../../image/IMG_0466.JPG"
					}
				],
				detailsList:[
				            "https://img.yzcdn.cn/upload_files/2018/08/30/FsV9nUCRJAQxqOwqp986fDPQCrkt.jpg",
				            "https://img.yzcdn.cn/upload_files/2018/08/30/FpFGkC8_hWSRaHvyce8rT7Tyd6_k.jpg",
				            "https://img.yzcdn.cn/upload_files/2018/08/30/Fm86-NxRtBogIeIJQQyxCUTMFGI9.jpg",
				            "https://img.yzcdn.cn/upload_files/2018/08/30/FjQ45h5N3iN6Kgz7gZrlO_tTQyke.jpg",
				            "https://img.yzcdn.cn/upload_files/2018/08/30/FrnDCNn66V_YWtbzDemGYafOa_N5.jpg",
				            "https://img.yzcdn.cn/upload_files/2018/08/30/FgoEfGkbtui-SdFdnEFkaNiMk-MP.jpg",
				            "https://img.yzcdn.cn/upload_files/2018/08/30/Fh5VEobiKh2MFK0saHJ14Or15AjR.jpg",
				
				        ],
				num: 0
			}
		},
		methods:{
			//轮播图高度自适应
			imgH(e) {
				console.log(e.detail.height)
				var winWid = uni.getSystemInfoSync().windowWidth;
				this.swiperHeight = e.detail.height / e.detail.width * winWid
			},
		}
	}
</script>

<style>
	.goods_info_top{
	    padding: 10px;
	    margin-bottom: 20px;
	    border-bottom: 1px solid #e5e5e5;
	}
	.goods_title{
	    font-size: 14px;
	    line-height: 20px;
	    height: 40px;
	    color: #5f5f5f;
	    padding-right: 70px;
	    position: relative;
	}
	.goods_collect_btn{
	    height: 40px;
	    width: 40px;
	    position: absolute;
	    right: 0px;
	    top: 0px;
	    border-left: 1px solid #E5E5E5;
	    text-align: center;
	    font-size: 12px;
	    line-height: 14px;
	}
	.goods_collect_btn text{
	    display: block;
	    width: 40px;
	}
	.goods_collect_btn image{
	    width: 24px;
	    height: 24px;
	    margin: 0 auto;
	}
	
	.goods_price{
	    font-size: 16px;
	    color:#ff0000;
	}
	.goods_old_price{
	    font-size: 12px;
	    color:#535353;
	    text-decoration: line-through;
	    margin-left: 10px;
	}
	.content{
	    margin-bottom: 60px;
	}
	.goods_bottom_btn{
	    position: fixed;
	    width: 100%;
	    z-index: 99;
	    bottom: 0px;
	    height: 50px;
	    background-color: #fff;
	    border-top: 1px solid #e5e5e5;
	}
	.goods_bottom_btn .btn{
	    width: 25%;
	    float: left;
	    text-align: center;
	    height: 50px;
	    line-height: 50px;
	    font-size: 12px;
	}
	.goods_bottom_btn .btn .box{
	    width: 25px;
	    height: 25px;
	    margin: 10px auto 0 auto;
	    position: relative;
	}
	.goods_num{
	    position: absolute;
	    top:0px;
	    right: -6px;
	    height: 12px;
	    line-height: 12px;
	    width: 12px;
	    color: #fff;
	    background-color: #ff0000;
	    border-radius: 50%;
	}
	.goods_bottom_btn .btn image{
	    width: 25px;
	    height: 25px;
	}
	.dv2{
	    background: rgba(16, 131, 131, 0.432);
	    color: #fff;
	}
	.dv3{
	    background: #FFA500;
	    color: #fff;
	}
	.dv4{
	    background: rgb(218, 67, 47);
	    color: #fff;
	}
</style>
