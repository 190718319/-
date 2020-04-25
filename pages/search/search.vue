<template>
	<view class="">
		<!--搜索框-->
		<view class="input">
		    <input class="weui-input" 
				placeholder-style="color:#a0a0a0" 
				placeholder="搜索目的地" 
				v-model="keyword"
				@confirm="search"
			/>
		    <image class="icon_search" src="../../static/image/search.png"></image>
			<view class="search_btn" @click="search">搜索</view>
		</view>
		<!--搜索框 end-->
		<!-- 搜索历史 -->
		<view class="search_history" v-if="dataList.length==0">
			<view class="history">搜索历史</view>
			<view 
			v-for="(item,index) in historyList" 
			:key="index" 
			class="history_item"
			@click="search(item)"
			>
				{{item}}
			</view>
		</view>
		<!-- 搜索历史 end-->
		<!-- 热门搜索 -->
		<view class="search_history" v-if="dataList.length==0">
			<view class="history">热门搜索</view>
			<view v-for="(item,index) in hot_List" :key="index" @click="search(item)" class="history_item">
				{{item}}
			</view>
		</view>
		<!-- 热门搜索 end-->
		<!-- 搜索结果列表 -->
		<view>
			<view class="scenicList" 
				v-for="(item, index) in dataList" 
				:key="item.sid"
				:data-sid="item.sid"
				@click="goDetail"
				v-if="dataList.length!=0">
				<image class="scenicImg" :src="item.imgurl" mode="widthFix"></image>
				<view style="font-size: 14px;">{{item.title}}</view>
				<view class="" style="font-size: 12px;color: #999999;">{{item.address}}</view>
			</view>
		</view>
		<!-- 搜索结果列表 end-->
	</view>
	
</template>

<script>
	import scenic from '../../static/js/scenic.js';
	export default{
		data(){
			return{
				keyword:'',
				dataList:[],
				historyList:["后庸关长城","广州中山纪念堂","广州","广东","深圳野生动物园"],
				hot_List:["后庸关长城","广州中山纪念堂","广州","广东","深圳野生动物园","动物园","热带","罗浮山","海南","福建","武当山"],
			}
		},
		methods:{
			//搜索功能
			search(item){
				let _this = this;
				let keyword = ''
				if(item){
					keyword = item
				}else{
					keyword = this.keyword
				}
				if(keyword){
					// this.dataList = scenic.result.filter(_=>_.title.includes(this.keyword)||_.address.includes(this.keyword))
					uni.request({
					    url: 'https://wxt.show/search/'+ keyword,
					    method: 'GET',
					    data: {},
					    success: res => {
					        this.dataList = res.data;
							if(this.dataList.length === 0){
								uni.showToast({
									title:'找不到你想要内容,请重新输入',
									icon:'none',
									duration: 2000
								})
							}else{
								uni.getStorage({
								    key: 'historyList',
								    success: function (history) {
										let historyData = history.data
										historyData.shift()
										historyData.unshift(_this.keyword)
										uni.setStorage({
										    key: 'historyList',
										    data: historyData,
										    success: function () {
												_this.historyList = history.data;
										    }
										});
								    }
								});
							}
					    },
					    fail: () => {},
					    complete: () => {}
					});
				}
				
			},
			//调整景点详情页
			goDetail(e){
				uni.navigateTo({
				    url: '../jingdianDetail/jingdianDetail?sid='+e.currentTarget.dataset.sid
				});
			}
		},
		watch:{
			keyword:function(val){
				if(!val){
					this.dataList= []
				}
			}
		},
		onLoad() {
			let _this = this;
			//首次进入判断historyList是否存在storage
			uni.getStorage({
			    key: 'historyList',
			    success: function (history) {
			    },
				fail:function(error){
					uni.setStorage({
					    key: 'historyList',
					    data: _this.historyList,
					    success: function () {
					    }
					});
				}
			});
		}
	}
</script>

<style lang="scss">
	.search_history{
		padding: 30rpx;
		font-size: 16px;
		&::after{
			content: "";
			display: block;
			clear: both;
		}
		.history_item{
			padding: 0 15px;
			float: left;
			background-color: #f3f5f7;
			text-align: center;
			line-height: 32px;
			border-radius: 5px;
			margin-right: 10px;
			margin-top: 10px;
			font-size: 14px;
			color: #666;
		}
	}
	.scenicList{
		text-align: center;
	}
	.scenicImg{
		width: 100px;
	}
	.input{
	    background-color: #f9f9f9;
	    height: 30px;
	    padding: 5px 60px 5px 20px;
	    position: relative;
		.search_btn{
			position: absolute;
			right: 15px;
			top: 8px;
			color: #999999;
			font-size: 16px;
		}
	}
	.weui-input{
	    background-color: #fff;
	    border-radius: 15px;
	    height: 30px;
	    line-height: 30px;
	    padding-left: 30px;
	    font-size: 14px;
	    
	}
	.input .icon_search{
	    position: absolute;
	    left: 28px;
	    top: 12px;
	    width: 16px;
	    height: 16px;
	}
</style>
