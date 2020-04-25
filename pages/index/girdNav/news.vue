<template>
    <view class="content">
		<!-- #ifdef H5 || APP-PLUS -->
		<view class="uni-list">
		    <view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in news_HA" :key="index" @click="opennews" :data-url="item.url">
		        <view class="uni-media-list">
		            <image class="uni-media-list-logo" :src="item.picUrl"></image>
		            <view class="uni-media-list-body">
		                <view class="uni-media-list-text-top title">{{item.title}}</view>
		                <view class="uni-media-list-text-bottom uni-ellipsis">{{item.ctime}}</view>
		            </view>
		        </view>
		    </view>
		</view>
		<!-- #endif -->
		<!-- #ifdef  MP -->
        <view class="uni-list">
            <view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in news_MP" :key="index" @tap="opennews" :data-postid="item.post_id">
                <view class="uni-media-list">
                    <image class="uni-media-list-logo" :src="item.author_avatar"></image>
                    <view class="uni-media-list-body">
                        <view class="uni-media-list-text-top title">{{item.title}}</view>
                        <view class="uni-media-list-text-bottom uni-ellipsis">{{item.created_at}}</view>
                    </view>
                </view>
            </view>
        </view>
		<!-- #endif -->
    </view>
</template>

<script>
    export default {
        data() {
            return {
                news_HA: [
					{ctime: "2020-04-11 00:00", title: "2020年共和国部长义务植树活动在京举行", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112584/1125842062_1586639273083_title0h.jpg", url: "http://travel.news.cn/2020-04/11/c_1125842062.htm"},
					{ctime: "2020-04-10 00:00", title: "【“疫”后花开 迈向诗和远方】美不胜收的云南迪庆 世界的香格里拉", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125839061_1586507603850_title0h.jpg", url: "http://travel.news.cn/2020-04/10/c_1125839061.htm"},
					{ctime: "2020-04-10 00:00", title: "【“疫”后花开 迈向诗和远方】千年淹城 梦回春秋", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125838014_1586506691448_title0h.jpg", url: "http://travel.news.cn/2020-04/10/c_1125838014.htm"},
					{ctime: "2020-04-10 00:00", title: "【“疫”后花开 迈向诗和远方】“齐鲁第一古村”朱家峪景区", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125837007_1586486526798_title0h.JPG", url: "http://travel.news.cn/2020-04/10/c_1125837007.htm"},
					{ctime: "2020-04-09 00:00", title: "【“疫”后花开 迈向诗和远方】远离繁杂感受静谧 根河源国家湿地公园", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125833500_1586417462833_title0h.JPG", url: "http://travel.news.cn/2020-04/09/c_1125833500.htm"},
					{ctime: "2020-04-09 00:00", title: "【“疫”后花开迈向诗和远方】不出国门体验异国风情 中俄边境旅游区", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125833453_1586417230392_title0h.jpg", url: "http://travel.news.cn/2020-04/09/c_1125833453.htm"},
					{ctime: "2020-04-09 00:00", title: "【“疫”后花开 迈向诗和远方】金坛茅山旅游度假区 风景这边正好", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125832620_1586412742864_title0h.jpg", url: "http://travel.news.cn/2020-04/09/c_1125832620.htm"},
					{ctime: "2020-04-09 00:00", title: "【“疫”后花开 迈向诗和远方】壶口“桃花汛” 大美吉县游", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125831666_1586395750322_title0h.jpeg", url: "http://travel.news.cn/2020-04/09/c_1125831666.htm"},
					{ctime: "2020-04-09 00:00", title: "北京玉渊潭公园4月11日起实施“实名制”网络预约购票", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112583/1125831049_1586394312503_title0h.jpg", url: "http://travel.news.cn/2020-04/09/c_1125831049.htm"},
					{ctime: "2020-04-08 00:00", title: "【“疫”后花开 迈向诗和远方】开封实景打造千年画卷《清明上河图》", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125828118_1586329271854_title0h.jpg", url: "http://travel.news.cn/2020-04/08/c_1125828118.htm"},
					{ctime: "2020-04-08 00:00", title: "【“疫”后花开 迈向诗和远方】福建尤溪古溪星河休闲旅游度假景区：舒适度假山林间", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125827092_1586314122387_title0h.jpg", url: "http://travel.news.cn/2020-04/08/c_1125827092.htm"},
					{ctime: "2020-04-08 00:00", title: "【“疫”后花开 迈向诗和远方】奇秀甲东南 福建武夷山", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125827278_1586314908169_title0h.jpg", url: "http://travel.news.cn/2020-04/08/c_1125827278.htm"},
					{ctime: "2020-04-08 00:00", title: "北京各大博物馆开展清明节线上文化活动", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125825532_1586306106221_title0h.jpg", url: "http://travel.news.cn/2020-04/08/c_1125825532.htm"},
					{ctime: "2020-04-08 00:00", title: "清明小长假全国铁路共发送旅客1136万人次", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125825563_1586306729204_title0h.jpg", url: "http://travel.news.cn/2020-04/08/c_1125825563.htm"},
					{ctime: "2020-04-08 00:00", title: "甘肃：六成A级景区开放 旅游“迎春回暖”", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125825562_1586306865204_title0h.jpg", url: "http://travel.news.cn/2020-04/08/c_1125825562.htm"},
					{ctime: "2020-04-08 00:00", title: "清明小长假北京市属公园游客量比去年同期少7成", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125825912_1586307007829_title0h.jpg", url: "http://travel.news.cn/2020-04/08/c_1125825912.htm"},
					{ctime: "2020-04-07 00:00", title: "【“疫”后花开 迈向诗和远方】“黔中一绝”天河潭", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125822140_1586232608453_title0h.jpg", url: "http://travel.news.cn/2020-04/07/c_1125822140.htm"},
					{ctime: "2020-04-07 00:00", title: "【“疫”后花开 迈向诗和远方】水润兴化 如诗如画", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125821704_1586229282092_title0h.jpg", url: "http://travel.news.cn/2020-04/07/c_1125821704.htm"},
					{ctime: "2020-04-07 00:00", title: "清明假期全国道路交通平稳有序", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125820799_1586222228580_title0h.jpg", url: "http://travel.news.cn/2020-04/07/c_1125820799.htm"},
					{ctime: "2020-04-07 00:00", title: "春暖花开待客来——福建旅游行业复工复产见闻", description: "旅游资讯", picUrl: "http://travel.news.cn/titlepic/112582/1125820789_1586222495191_title0h.jpg", url: "http://travel.news.cn/2020-04/07/c_1125820789.htm"},
				],
				news_MP: []
			};
        },
		methods:{
		    opennews(e){
				//#ifdef H5 || APP-PLUS
		        uni.navigateTo({
		            url: './newsDeteil?url='+e.currentTarget.dataset.url,
					animationType:"pop-in",
		        });
				//#endif
				//#ifdef  MP 
				uni.navigateTo({
					url: './newsDeteil?postid='+e.currentTarget.dataset.postid
				});
				//#endif
		    }
		},
        onLoad:function(){
				//#ifdef H5 || APP-PLUS
     //        uni.request({
     //            url: 'http://api.tianapi.com/travel/index?key=0652fd9507a9aeacd0371e519feb89e6&num=20',
     //            method: 'GET',
     //            data: {},
     //            success: res => {
					// console.log(res)
     //                this.news_HA = res.data.newslist;
     //            },
     //            fail: () => {},
     //            complete: () => {}
     //        });
				//#endif 
				//#ifdef  MP 
				uni.request({
				    url: 'https://unidemo.dcloud.net.cn/api/news',
				    method: 'GET',
				    data: {},
				    success: res => {
				        this.news_MP = res.data;
				    },
				    fail: () => {},
				    complete: () => {}
				});
				//#endif 
        }
    }
</script>

<style lang="scss">
	.uni-media-list{
		background-color: #f6f6f6;
		overflow: hidden;
		margin-bottom: 10px;
		display: flex;
		.uni-media-list-body{
			margin-top: 5px;
			height: 170rpx;
			flex: auto;
			.title{
				overflow: hidden;
				text-overflow: ellipsis;
				display:-webkit-box; 
				-webkit-box-orient:vertical;
				-webkit-line-clamp:2; 
			}
		}
	}
	.uni-media-list-logo{
		flex: 0 0 150rpx;
		height: 150rpx;
		margin: 10px;
		border-radius: 20rpx;
	}
    .uni-media-list-body{height: auto;}
    .uni-media-list-text-top{line-height: 1.6em;}
</style>