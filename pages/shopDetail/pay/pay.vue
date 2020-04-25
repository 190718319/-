<template>
	<view id="pay">
		<view class="address" bindtap="getAddress">
		    <block  v-if="address">
		        <image src="../../../static/image2/icon-dw.png" class="iconAddress"></image>
		        <view class="pay_content" >
		            <view class="name">
		                <text> {{address.username}}</text> 
		                <text> {{address.usertel}}</text>
		            </view>
		            <view class="dw">
		                <text>{{address.addressdetail}}</text>
		            </view>
		        </view>
		        <image src="../../../static/image2/icon-arrow.png" class="iconArrow"></image>
		    </block>
		    <block v-if="!address" >
		        <image style="margin-top:10px;" src="../../../static/image2/icon-dw.png" class="iconAddress"></image>
		        <view class="pay_content" >
		            <view class="name">
		                <text style="margin-left:50px;line-height:40px;"> 点击前往选择地址</text> 
		            </view>
		        </view>
		        <image src="../../../static/image2/icon-arrow.png" class="iconArrow"></image>
		    </block>
		    
		</view>
		
		<!-- 商品列表 -->
		<view class="pay_order">
		    <view class="thead tr">
		        <view class="td">
		            商品
		        </view>
		        <view class="td">
		            数量
		        </view>
		        <view class="td">
		            单价
		        </view>
		    </view>
		    <view class="tbody tr" v-for="(item,index) in goodsList" :key="index">
		        <view class="td">
		            {{item.carName}}
		        </view>
		        <view class="td">
		            {{item.carNum}}
		        </view>
		        <view class="td">
		            {{item.carPrice}}
		        </view>
		    </view>
		</view>
		
		
		<view class="pay_remarks">
		    <input placeholder="填写备注" type="text"></input>
		</view>
		
		
		
		<view class="car_bot">
		    <view class="car_bot_wrap">
		        总价 <text class="car_total_monay">￥288.00</text>
		        <view class="car_order_confirm" bindtap="pay">支付</view>
		    </view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				goodsList:[],
				address: null  //地址
			}
		}
	}
</script>

<style>
	/* pages/pay/pay.wxss */
	page{
	    background-color: #F5F6F7;
	}
	.address{
	    padding:10px;
	    position: relative;
	    background: #fff;
	    margin-bottom: 10px;
	    height: 40px;
	}
	.address image{
	    width:20px;
	    height: 20px;
	    position: absolute;
	    top:10px;
	    left: 10px;
	}
	.pay_content{
	    margin:0px 30px;
	}
	.address .dw{
	    font-size: 12px;
	}
	.address image.iconArrow{
	    left:auto;
	    top:20px;
	    right: 20px;
	}
	
	.pay_order{
	    background: #fff;
	    margin-bottom: 10px;
	}
	.pay_order .thead{
	    padding: 10px;
	    font-size: 14px;
	    border: 1px solid #e5e5e5;
	}
	.pay_order .tr .td{
	    display: inline-block;
	    width: 33.33%;
	
	    overflow: hidden;
	    text-overflow: ellipsis;
	    white-space: nowrap;
	}
	
	.pay_order .tbody{
	    padding:5px;
	    font-size: 12px;
	    margin-bottom: 1px;
	}
	.pay_order .tr .td:nth-child(1){
	    width: 60%;
	}
	.pay_order .tr .td:nth-child(2){
	    width: 20%;
	}
	.pay_order .tr .td:nth-child(3){
	    width: 20%;
	}
	
	.pay_remarks{
	    background: #fff;
	    height: 40px;
	    line-height: 40px;
	}
	.pay_remarks input{
	    height: 40px;
	    line-height: 40px;
	    padding-left: 20px;
	}
	
	
	.car_bot{
	    position: fixed;
	    width:100%;
	    background-color: #fff;
	    bottom:0px;
	    border-bottom: 1px solid #e5e5e5;
	    font-size: 14px;
	}
	.car_bot_wrap{
	    padding:10px;
	    height: 30px;
	    line-height: 30px;
	
	}
	.car_total_monay{
	    color:#ff0000;
	    margin-left:5px;
	}
	.car_order_confirm{
	    float:right;
	    background: #ff7e3a;
	    color:#fff;
	    width: 80px;
	    text-align: center;
	}

</style>
