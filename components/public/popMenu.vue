<template>
	<view class="popMenu">
		<!-- 悬浮按钮 -->
		<uni-fab
			popMenu
			:pattern="pattern"
			:content="content"
			vertical="bottom"
			horizontal="right"
			direction="vertical"
			@trigger="trigger"
		></uni-fab>
		<!-- <uni-fab @fabClick="fabClick"></uni-fab> -->
	</view>
</template>

<script>
	export default{
		data:function(){
			return{
				pattern:{  //悬浮按钮样式
					buttonColor:"rgba(48,122,255,.7)"
				},
				content:[
					{
						iconPath:"../../static/image2/faxian.png",
						text:"发表攻略"
					},{
						iconPath:"../../static/image2/faxian.png",
						text:"提交问答"
					},
				]//悬浮按钮内容
			}
		},
		methods:{
			trigger(event){
				switch(event.index){
					case 0:
						console.log("发表攻略");
							break;
					case 1:
						console.log("发起问题");
						uni.navigateTo({
							url:"../../pages/QA/QAdetail/newQA"
						})
							break;
				}
			}
		},
	}
</script>

<style>
</style>
