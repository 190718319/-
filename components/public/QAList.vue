<template>
	<view class="">
		<view class="item" v-for="(item,index) in QAList" :key="index" @click="goQAdetail">
			<view class="title">
				{{item.title}}
			</view>
			<view class="content">
				{{item.content}}
			</view>
			<view class="time">
				{{item.time}} | 回答 {{item.answer?item.answer.length:0}}
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data() {
			return {
				QAList:[
					{
						title:"被携程误导选择了退票",
						content:"前几天在携程网站订购了新西兰奥克兰飞往上海浦东机场的机票，被告知航班取消，退票时提示改签时间会过长，建议退票重新订购，我就选择了退票，紧接着又订购了一张6月4号的机票，结果被告知有退票费，是你们取消了航班，何来退票费一说，如果不是看到提示建议退票重新订购，我完全可以选择改签，现在手上抓着两张机票，我该怎么办呢！",
						time:"2020.04.11",
						answer: [3]
					},{
						title:"请问，有谁知道，在香港领结婚证需要体检报告吗？",
						content:"请问，有谁知道，在香港领结婚证需要体检报告吗？",
						time:"2020.04.11",
					},{
						title:"现在从越南胡志明市怎么回中国?",
						content:"现在从越南胡志明市怎么回中国?",
						time:"2020.04.11",
					},{
						title:"南昌机场到南昌西高铁站坐机场大巴要多久？",
						content:"南昌机场到南昌西高铁站坐机场大巴要多久？",
						time:"2020.04.11",
					},{
						title:"喳呀山风景区停车被罚款？",
						content:"景区外路边停车去售票大厅问情况回来被贴条罚200元妈妈的城管执法管到几十里外的景区了外地车第一次来时要考虑一下",
						time:"2020.04.11",
					}
				]
			}
		},
		methods:{
			goQAdetail(){
				uni.navigateTo({
					url:"../../pages/QA/QAdetail/QAdetail"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.item{
		margin-top: 15rpx;
		background-color: #FFFFFF;
		padding: 10px 30rpx;
		.title{
			line-height: 30px;
			margin: 5px 0;
			font-size: 18px;
			font-weight: bold;
			color: #333333;
		}
		.content{
			font-size: 16px;
			line-height: 24px;
			color: #666666;
			max-height: 70px;
			overflow: hidden;
			word-break: break-all;  /* break-all(允许在单词内换行。) */
			text-overflow: ellipsis;  /* 超出部分省略号 */
			display: -webkit-box; /** 对象作为伸缩盒子模型显示 **/
			-webkit-box-orient: vertical; /** 设置或检索伸缩盒对象的子元素的排列方式 **/
			-webkit-line-clamp: 3; /** 显示的行数 **/
		}
		.time{
			font-size: 12px;
			color: #999999;
			line-height: 40px;
		}
	}
	
</style>
