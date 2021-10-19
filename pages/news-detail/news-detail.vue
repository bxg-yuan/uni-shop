<template>
	<view class="news_detail">
		<text class="title">{{detail.title}}</text>
		<view class="info">
			<text>发表时间：{{detail.add_time|formatDate}}</text>
			<text>浏览次数：{{detail.click}}</text>
		</view>
		<view class="content">
			<rich-text :nodes="detail.content"></rich-text>
		</view>
	</view>
</template>

<script>
	import CONFIG from '../../config/news.js';
	
	export default {
		data() {
			return {
				id: 0,
				detail: CONFIG.newsDetail[0]
			}
		},
		methods: {
			// 有接口的情况下可请求接口获取数据
			// async getNewsDetail() {
			// 	const res = await this.$myRequest({
			// 		url: '/xxx/xxx'+this.id
			// 	});
			// 	this.detail = res.data.message[0];
			// }
		},
		onLoad(options) {
			this.id = options.id;
			// this.getNewsDetail()
		}
	}
</script>

<style lang="scss">
	.news_detail {
		font-size: 30rpx;
		padding: 0 20rpx;
		.title {
			text-align: center;
			width: 710rpx;
			display: block;
			margin: 20rpx 0 40rpx 0;
			font-weight: bold;
		}
		.info {
			display: flex;
			justify-content: space-between;
			color: #708090;
		}
		.content {
			margin-top: 20rpx;
		}
	}
</style>
