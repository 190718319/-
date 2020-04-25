<template>
	<view id="guide">
		<guide-list></guide-list>
	</view>
</template>

<script>
	import guideList from '../../components/public/guideList.vue';
	export default{
		components:{
			guideList
		},
	}
</script>

<style lang="scss" scoped>
	#guide{
		padding: 0 30rpx;
	}
	
</style>
