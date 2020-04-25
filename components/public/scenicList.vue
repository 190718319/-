<template>
	<!-- 景区推荐 -->
	<view>
		<view class="scenicList" 
			v-for="(item, index) in scenicList" 
			:key="item.sid"
			:data-sid="item.sid"
			@click="goDetail"
			>
			<image class="scenicImg" :src="item.imgurl" mode="widthFix"></image>
			<view class="star" v-if="item.grade">{{item.grade}}级</view>
			<view style="font-size: 14px;">{{item.title}}</view>
			<view class="" style="font-size: 12px;color: #999999;">地址:{{item.address}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				scenicList:[
					{
						"title": "广东韶关丹霞山(丹霞地貌命名地)",
						"grade": "AAAAA",
						"price_min": "39",
						"comm_cnt": null,
						"cityId": "90",
						"address": "广东省韶关市仁化县丹霞山",
						"sid": "31723",
						"url": "http://www.ly.com/scenery/BookSceneryTicket_31723.html",
						"imgurl": "http://pic4.40017.cn/scenery/destination/2016/09/24/14/OScgQf_240x135_00.jpg"
					},
					{
						"title": "梦幻百花洲",
						"grade": "",
						"price_min": "25",
						"comm_cnt": null,
						"cityId": "78",
						"address": "广东东莞市松山湖工业园核心区域内",
						"sid": "26515",
						"url": "http://www.ly.com/scenery/BookSceneryTicket_26515.html",
						"imgurl": "http://pic4.40017.cn/scenery/destination/2016/08/22/11/UPT16K_240x135_00.jpg"
					},
					{
						"title": "高明盈香生态园",
						"grade": "AAAA",
						"price_min": "80",
						"comm_cnt": null,
						"cityId": "79",
						"address": "广东省佛山市高明区荷城街道西安冼村",
						"sid": "29961",
						"url": "http://www.ly.com/scenery/BookSceneryTicket_29961.html",
						"imgurl": "http://pic5.40017.cn/01/001/1d/be/rBANC1jfdkKAWRw6AAQAAM7Uuqs404_240x135_00.jpg"
					},
					{
						"title": "余荫山房",
						"grade": "",
						"price_min": "9",
						"comm_cnt": null,
						"cityId": "80",
						"address": "广东省广州市番禺区南村镇北大街余荫山房",
						"sid": "4038",
						"url": "http://www.ly.com/scenery/BookSceneryTicket_4038.html",
						"imgurl": "http://pic4.40017.cn/scenery/destination/2017/02/24/16/AiaIz6_240x135_00.jpg"
					},
					{
						"title": "深圳野生动物园",
						"grade": "AAAA",
						"price_min": "120",
						"comm_cnt": null,
						"cityId": "91",
						"address": "广东省深圳市南山区西丽湖路4065号",
						"sid": "3714",
						"url": "http://www.ly.com/scenery/BookSceneryTicket_3714.html",
						"imgurl": "http://pic4.40017.cn/scenery/destination/2017/03/01/11/HEl2Qf_240x135_00.jpg"
					},
					{
						"title": "深圳青青世界",
						"grade": "AAAA",
						"price_min": "4",
						"comm_cnt": null,
						"cityId": "91",
						"address": "广东省深圳市南山区月亮湾青青路1号",
						"sid": "3696",
						"url": "http://www.ly.com/scenery/BookSceneryTicket_3696.html",
						"imgurl": "http://pic4.40017.cn/scenery/destination/2017/02/28/13/HC0ce3_240x135_00.jpg"
					}
				]
			}
		},
		methods:{
			goDetail(e){
				uni.navigateTo({
				    url: '../../pages/jingdianDetail/jingdianDetail?sid='+e.currentTarget.dataset.sid
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	.scenicList{
		padding: 30rpx;
		.scenicImg{
			width: 100%;
		}
	}
</style>
