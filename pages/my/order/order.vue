<template>
	<view id="order">
		<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem"></uni-segmented-control>
		<view class="content">
			
			<!-- 商品列表 -->
			<view class="goods_list" v-for="(item1,index1) in goodsList" :key="index1">
				<uni-list>
					<uni-list-item :title="'订单号:'+item1.id" :rightText="'状态:'+item1.status"></uni-list-item>
				</uni-list>
			    <view v-for="(item,index) in item1.goods" :key="index" class="li">
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
			            <view class="car_item_operate">
			                <text class="num">数量:{{item.carNum}}</text>
			            </view>
			        </view>
			    </view>
			    <view class="btnbox" v-if="item1.status == '待收货'">
			        <button 
			            type="primary"
			            bindtap="tofinish" 
			            :data-id="item1.id"
			        >确认收货</button>
			        <button 
			            bindtap="del" 
			            :data-id="item1.id"
			        >删除订单</button>
			    </view>
			    <view class="btnbox" v-if="item1.status == '已完成'">
			        <button >商品评价</button>
			        <button 
			            bindtap="del" 
			            :data-id="item1.id"
			        >删除订单</button>
			    </view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
	    data() {
	        return {
	            items: ['全部订单','待收货','已完成'],
	            current: 0,
				goodsList:[
					{
						id:123123123,
						status:"待收货",
						goods:[
							{
								carName: "花芽原创设计美人鱼耳夹女纯银日韩学生长款流苏无耳洞耳骨夹耳饰",
								carPrice: '28',
								carImage: "../../../static/image2/goodslist02.jpg",
								carNum:1
							},{
								carName: "花芽原创设计美人鱼耳夹女纯银日韩学生长款流苏无耳洞耳骨夹耳饰",
								carPrice: '28',
								carImage: "../../../static/image2/goodslist02.jpg",
								carNum:2
							}
						]
					},{
						id:123123123,
						status:"已完成",
						goods:[
							{
								carName: "花芽原创设计美人鱼耳夹女纯银日韩学生长款流苏无耳洞耳骨夹耳饰",
								carPrice: '28',
								carImage: "../../../static/image2/goodslist02.jpg",
								carNum:1
							},{
								carName: "花芽原创设计美人鱼耳夹女纯银日韩学生长款流苏无耳洞耳骨夹耳饰",
								carPrice: '28',
								carImage: "../../../static/image2/goodslist02.jpg",
								carNum:2
							}
						]
					},
				]
	        }
	    },
	    methods: {
	        onClickItem(e) {
	            if (this.current !== e.currentIndex) {
	                this.current = e.currentIndex;
	            }
	        }
	    }
	}
</script>

<style>
	
	.goods_list .li{
	    position: relative;
	    height: 100px;
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
	    /* margin-top: -15px; */
	    margin-left:100px;
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
	.num{
	    float: right;
	    display: block;
	    height: 14px;
	    text-align: center;
	    line-height: 14px;
	    color:#929292;
	    margin: -5px 10px 0 0;
	}
	.btnbox{
	    height: 50px;
	
	}
	.btnbox button{
	    width: 80px;
	    font-size: 14px;
	    font-weight: normal;
	    float: right;
	    padding: 0;
	    margin: 0;
	    line-height: 30px;
	    margin-left: 10px;
	}
</style>
