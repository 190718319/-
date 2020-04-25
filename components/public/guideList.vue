<template>
	<view class="">
		<view class="guideList">
			<view class="item" v-for="(item,index) in guideList" :key="index">
				<view class="content clearfix">
					<view class="img fl">
						<image :src="item.image"></image>
					</view>
					<view class="title fl">
						{{item.title}}
					</view>
				</view>
				<view class="info">
					<image :src="item.tx_img" mode=""></image>
					<view class="name">{{item.name}}</view>
					<view class="time">发布于{{item.time}}</view>
					<view><uni-icons type="hand-thumbsup" size="14"></uni-icons>153</view>
					<view><uni-icons type="chat" size="14"></uni-icons>327</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data() {
			return {
				guideList:[
					{
						image:"http://pic4.40017.cn/scenery/destination/2016/08/30/20/mhUEBC_240x135_00.jpg",
						title:"【新疆之美，中国之傲！】【新疆之美，中国之傲！】2019金秋喀纳斯环线（五彩滩、白哈巴、喀纳斯、禾木、可可托海、博斯腾湖、塔里木胡杨林）",
						tx_img:"../../static/image/banner03.jpeg",
						name:"1简单就是快乐",
						time:"2020年03月22日"
					},{
						image:"http://pic4.40017.cn/scenery/destination/2016/08/30/20/mhUEBC_240x135_00.jpg",
						title:"2019金秋喀纳斯环线（五彩滩、白哈巴、喀纳斯、禾木、可可托海、博斯腾湖、塔里木胡杨林）",
						tx_img:"../../static/image/banner03.jpeg",
						name:"2简单就是快乐",
						time:"2020年03月22日"
					},{
						image:"http://pic4.40017.cn/scenery/destination/2016/08/30/20/mhUEBC_240x135_00.jpg",
						title:"【新疆之美，中国之傲！】2019金秋喀纳斯环线",
						tx_img:"../../static/image/banner03.jpeg",
						name:"3简单就是快乐",
						time:"2020年03月22日"
					},{
						image:"http://pic4.40017.cn/scenery/destination/2016/08/30/20/mhUEBC_240x135_00.jpg",
						title:"【新疆之美，中国之傲！】（五彩滩、白哈巴、喀纳斯、禾木、可可托海、博斯腾湖、塔里木胡杨林）",
						tx_img:"../../static/image/banner03.jpeg",
						name:"2简单就是快乐",
						time:"2020年03月22日"
					},{
						image:"http://pic4.40017.cn/scenery/destination/2016/08/30/20/mhUEBC_240x135_00.jpg",
						title:"【新疆之美，中国之傲！】2019金秋喀纳斯环线（五彩滩、白哈巴、喀纳斯、禾木、可可托海、博斯腾湖、塔里木胡杨林）",
						tx_img:"../../static/image/banner03.jpeg",
						name:"3简单就是快乐",
						time:"2020年03月22日"
					}
				]
			}
		}
	}
</script>

<style lang="scss">
	.item{
		padding: 0 30rpx;
		margin-top: 15px;
		border-bottom: 1px solid #CCCCCC;
		padding-bottom: 15px;
		&:last-child{
			border-bottom: 0;
		}
		.content{
			display: flex;
			margin-bottom: 5px;
			.img{
				width: 35%;
				margin-right: 5%;
				// height: 150px;
				text-align: center;
				image{
					width: 100%;
					height: 100px;
					border-radius: 10px;
				}
			}
			.title{
				width: 60%;
				font-size: 16px;
				line-height: 24px;
				color: #444444;
				height: 100px;
				overflow: hidden;
				word-break: break-all;  /* break-all(允许在单词内换行。) */
				text-overflow: ellipsis;  /* 超出部分省略号 */
				display: -webkit-box; /** 对象作为伸缩盒子模型显示 **/
				-webkit-box-orient: vertical; /** 设置或检索伸缩盒对象的子元素的排列方式 **/
				-webkit-line-clamp: 4; /** 显示的行数 **/
			}
		}
		
		.info{
			font-size: 14px;
			color: #999999;
			display: flex;
			justify-content: space-between;
			image{
				width: 18px;
				height: 18px;
				border-radius: 50%;
				vertical-align: bottom;
			}
			view{
				margin-right: 20rpx;
				&.name{
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
	}
</style>
