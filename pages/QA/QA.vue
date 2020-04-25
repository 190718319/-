<template>
	<view id="QA">
		<!--搜索框-->
		<view class="input">
			<input class="weui-input" placeholder-style="color:#a0a0a0" placeholder="搜索问答" />
			<image class="icon_search" src="../../static/image/search.png"></image>
		</view>
		<!--搜索框 end-->
		<!-- 问答列表 -->
		<qa-list></qa-list>
		<!-- 悬浮按钮 -->
		<popmenu></popmenu>
		<!-- <uni-fab @fabClick="fabClick"></uni-fab> -->
	</view>
</template>

<script>
	import qaList from '../../components/public/QAList.vue';
	import popmenu from '../../components/public/popMenu.vue';
	export default{
		components:{
			qaList,
			popmenu
		},
		data(){
			return{
				
			}
		},
		
	}
</script>

<style lang="scss" scoped>
	#QA{
		background-color: rgb(241,241,241);
	}
	.input {
		background-color: #fff;
		height: 30px;
		padding: 5px 20px;
		position: relative;
	}
	
	.weui-input {
		background-color: rgb(249,249,249);
		border-radius: 15px;
		height: 30px;
		line-height: 30px;
		padding-left: 30px;
		font-size: 14px;
	
	}
	
	.input .icon_search {
		position: absolute;
		left: 28px;
		top: 12px;
		width: 16px;
		height: 16px;
	}
	
	
</style>
