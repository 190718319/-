<template>
	<view class="newQA">
		<input class="title" type="text" v-model="title" placeholder="请用简洁的文字清晰的描述你的问题"/>
		<textarea class="content" v-model="content" placeholder="请详细描述你的问题" />
		<view class="tips">
			提示：请勿发布与旅行无关的问题，转让/广告等不良信息将被删除。
		</view>
		<button type="default" @click="newQA">提交问题</button>
	</view>
</template>

<script>
	export default{
		data:function(){
			return {
				title:'',
				content:''
			}
		},
		methods:{
			newQA(){
				if(this.title && this.content){
					uni.request({
					    url: 'https://www.wxt.show/newQA',
						header:{
							'Content-Type': 'application/json'
						},	
						data: {
							title:this.title,
							content:this.content
						},
						method:"POST",
						success(res) {
							this.title='';
							this.content='';
							uni.showToast({
								title:res.data.msg,
								icon:'none',
								duration: 2000
							})
							
						}
					})
				}else{
					uni.showToast({
						title:'请输入标题跟内容,再次提交',
						icon:'none',
						duration: 1500
					})
				}
			}
		}
	}
</script>
	
<style lang="scss">
	.newQA{
		padding: 30rpx;
		.title{
			border: 1px solid #CCCCCC;
			height: 30px;
			border-radius: 5px;
			margin-bottom: 10px;
			font-size: 14px;
			padding:0 10px;
		}
		.content{
			border: 1px solid #CCCCCC;
			background-color: #F8F8F8;
			width: 100%;
			border-radius: 5px;
			font-size: 14px;
			box-sizing: border-box;
			padding:0 10px;
		}
		.tips{
			font-size: 14px;
			color: #999;
			margin: 20px 0;
		}
		button{
			font-size: 14px;
		}
	}
</style>
