<template>
	<view class="">
		
	<view class="QAdetail">
		<view class="title">
			{{QAdetail.title}}
		</view>
		<view class="content">
			{{QAdetail.content}}
		</view>
		<view class="info">
			<image :src="QAdetail.tx_url" mode=""></image>
			<view class="username">{{QAdetail.username}}</view>
			<view class="time">提问于{{QAdetail.time}}</view>
			<view><uni-icons type="hand-thumbsup" size="14"></uni-icons>{{QAdetail.good_num}}</view>
		</view>
		<view class="allAnswer">
			全部回答（{{QAdetail.answerList.length}}）
		</view>
		<!-- 评论列表 -->
		<view class="answerList " v-for="(items,index) in QAdetail.answerList" :key="index">
			<view class="userinfo clearfix">
				<image :src="items.tx_url" mode=""></image>
				<text class="username">{{items.username}}</text>
				<view class="right"><uni-icons color="#11BF79" type="hand-thumbsup" size="14"></uni-icons>{{items.good_num}}</view>
			</view>
			<view class="answer">
				{{items.answer}}
			</view>
			<view class="time">
				{{items.time}}
			</view>
		</view>
		
		<view class="isBottom">
			没有更多评论
		</view>
	</view>
	<view class="input">
		<input type="text" confirm-type="send" placeholder="回答TA"/>
		<view class="send" type="default">发送</view>
	</view>
	</view>
</template>

<script>
	export default{
		data:function(){
			return {
				QAdetail:{
					title:"摩洛哥转机有什么限制",
					content:"从摩洛哥转机,现在有什么限制吗?",
					tx_url:"https://pic.qyer.com/avatar/007/34/46/13/48?v=1471226586",
					username:"我coo故我在",
					good_num:"153",
					time:"2小时前",
					answerList:[
						{
							tx_url:"https://pic.qyer.com/avatar/008/28/81/30/48?v=1474868259",
							username:"我coo故我在",
							good_num:"13",
							answer:"没有限制但是没有飞国内的航线了",
							time:"2小时前"
						},{
							tx_url:"https://pic.qyer.com/avatar/008/28/81/30/48?v=1474868259",
							username:"我coo故我在",
							good_num:"13",
							answer:"没有限制但是没有飞国内的航线了",
							time:"2小时前"
						},{
							tx_url:"https://pic.qyer.com/avatar/008/28/81/30/48?v=1474868259",
							username:"我coo故我在",
							good_num:"13",
							answer:"没有限制但是没有飞国内的航线了",
							time:"2小时前"
						},{
							tx_url:"https://pic.qyer.com/avatar/008/28/81/30/48?v=1474868259",
							username:"我coo故我在",
							good_num:"13",
							answer:"没有限制但是没有飞国内的航线了",
							time:"2小时前"
						}
					]
				}
			}
		}
	}
</script>

<style lang="scss">
	.QAdetail{
		padding: 10px 30rpx 60px;
		.title{
			font-weight: bold;
			font-size: 16px;
			line-height: 32px;
			margin-bottom: 10px;
		}
		.content{
			font-size: 14px;
			margin-bottom: 20px;
		}
		.info{
			font-size: 14px;
			color: #999999;
			display: flex;
			justify-content: space-between;
			margin-bottom: 30px;
			image{
				margin-top: -4px;
				width: 26px;
				height: 26px;
				border-radius: 50%;
				vertical-align: super;
			}
			view{
				margin-right: 20rpx;
				&.username{
					display: inline-block;
					margin-bottom: -4px;
					width: 70px;
					overflow: hidden;
					text-overflow: ellipsis;
					white-space: nowrap;
				}
				&:last-child{
					margin-right:0 ;
				}
			}
		}
		.allAnswer{
			font-size: 14px;
		}
		.answerList{
			margin-top: 15px;
			border-top: 1px solid #CCCCCC;
			image{
				margin-top: 10px;
				margin-right:15px ;
				width: 36px;
				height: 36px;
				border-radius: 50%;
				line-height: 50px;
				float: left;
			}
			.username{
				font-size: 14px;
				line-height: 50px;
				float: left;
			}
			.right{
				float: right;
				font-size: 12px;
				color:#11BF79;
				height: 30px;
				line-height: 30px;
				border-radius: 20%;
				margin-top: 10rpx;
			}
			.answer{
				font-size: 14px;
				margin-bottom: 15px;
			}
			
			.time{
				font-size: 12px;
				color: #999999;
			}
		}
		.isBottom{
			text-align: center;
			font-size: 14px;
			color: #999999;
			border-top: 1px solid #ccc;
			margin-top: 20px;
			padding-top: 20px;
		}
	}
	.input{
		position: fixed;
		bottom: 0;
		left: 0;
		background-color: skyblue;
		height: 50px;
		line-height: 50px;
		width: 100%;
		padding-left: 20px;
		padding-right: 60px;
		box-sizing: border-box;
		input{
			display: inline-block;
			border-radius: 15px;
			background-color: #FFFFFF;
			width: 100%;
			height: 30px;
			margin-top: 10px;
			padding-left: 30px;
			box-sizing: border-box;
		}
		.send{
			position: absolute;
			right: 20px;
			bottom: 0px;
			font-size: 14px;
		}
	}
	
</style>
