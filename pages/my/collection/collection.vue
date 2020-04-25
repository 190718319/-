<template>
	<view id="collection">
		<view class="goods_list" v-for="(item,index) in goodsList" :key="index">
		    <view class="left">
		        <image :src="item.carImage"></image>
		    </view>
		    <view class="right">
		            <view class="goods_name">
		                <text>{{item.carName}}</text>
		            </view>
		            <view class="goods_price">
		                <text>￥{{item.carPrice}}</text>
		            </view>
		            <view class="cart">
		                <image src="../../../static/image2/shanchu.png" bindtap="carDel" :data-id="index"></image>
		            </view>
		    </view>
		</view>
		<!-- 商品列表 end-->
		<view v-if="goodsList.length == 0" style="margin:50px auto 0;text-align:center;font-size:14px;color:#999;">
		    那么多好看的饰品竟然没有你喜欢的,<text style="text-decoration: underline; color:blue" bindtap="getIndex" >去逛逛</text>
		</view>
		
		<view class="empty-div" v-if="goodsList.length == 0">
		    <image src="../../../static/image2/empty.png" mode="widthFix"></image>
		    <view class="empty-tip">暂无收藏商品</view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				goodsList:[
					{
						carName: "花芽原创设计美人鱼耳夹女纯银日韩学生长款流苏无耳洞耳骨夹耳饰",
						carPrice: '28',
						carImage: "../../../static/image2/goodslist02.jpg",
					},{
						carName: "花芽原创设计美人鱼耳夹女纯银日韩学生长款流苏无耳洞耳骨夹耳饰",
						carPrice: '28',
						carImage: "../../../static/image2/goodslist02.jpg",
					}
				]
			}
		}
	}
</script>

<style>
	.goods_list{
	    height: 100px;
	    padding-left:100px;
	    position: relative;
	}
	.left {
	    position: absolute;
	    top:10px;
	    left: 10px;
	}
	
	.left image{
	    width: 80px;
	    height: 80px;
	}
	
	.right{
	    padding:10px 0;
	    height: 80px;
	    /* overflow: hidden; */
	}
	.goods_name{
	    font-size: 14px
	}
	.goods_address{
	    color:#929292;
	    font-size: 12px;
	}
	.goods_price{
	    font-size: 14px;
	    color:#F47378;
	    width: 100%;
	    line-height: 22px;
	    height: 22px;
	    margin-top: 5px;
	}
	.cart{
	    position: absolute;
	    right: 10px;
	    bottom:10px;
	}
	.cart image{
	    width: 20px;
	    height: 20px;
	}
	
	.empty-div image {
	    display: block;
	    margin: 100px auto 0;
	    width: 50%;
	}
	.empty-tip{
	    text-align: center;
	    color: #cccccc;
	    font-size: .4375rem;
	}

</style>
