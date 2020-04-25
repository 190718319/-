
<template>
    <view>
		<!-- #ifdef H5 || APP-PLUS -->
			<web-view class="web-view" :src="url" :webview-styles="webviewStyles"></web-view>
		<!-- #endif -->
		<!-- #ifdef  MP -->
			<view class="wrap">
				<view class="title">
					{{title}}
				</view>
				<view class="content">
					<rich-text :nodes="content"></rich-text>
				</view>
			</view>
		<!-- #endif -->
	</view>
</template>
<script>
    export default {
        data() {
            return {
				//H5 || APP-PLUS
				url:'', 
				webviewStyles: {
					progress: {
						color: 'lightblue'
					}
				},
				//MP
				title: '',
				content: ''
            };
        },
		onLoad:function(option){ //option为object类型，会序列化上个页面传递的参数
			// #ifdef H5 || APP-PLUS
			console.log(option.url); //打印出上个页面传递的参数。
			this.url = option.url;
			// #endif
			// #ifdef  MP 
			uni.request({
			    url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+ option.postid,
			    method: 'GET',
			    data: {},
			    success: res => {
			        this.title = res.data.title;
			        this.content = res.data.content;
					console.log(res.data)
			    },
			    fail: () => {},
			    complete: () => {}
			});
			// #endif
		}
    }
</script>

<style>
    /* .wrap{padding: 10upx 2%;width: 96%;flex-wrap: wrap;}
    .title{line-height: 2em;font-weight: bold;font-size: 40upx;}
    .content{line-height: 2em;} */
	.web-view{
		margin-top: -50px;
	}
	.wrap{padding: 10upx 2%;width: 96%;flex-wrap: wrap;}
	.title{line-height: 2em;font-weight: bold;font-size: 40upx;}
	.content{line-height: 2em;}
</style>