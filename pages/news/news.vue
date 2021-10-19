<template>
	<view class="news">
		<news-item :list="newsList" @itemClick="goDetail"></news-item>
	</view>
</template>

<script>
	import CONFIG from '../../config/news.js';
	import newsItem from '../../components/news-item/news-item.vue';
	
	export default {
		data() {
			return {
				newsList: CONFIG.newsList
			}
		},
		methods: {
			// 有接口的情况下请求接口获取数据
			// getNews() {
			// 	const res = this.$myRequest({
			// 		url: '/xxx/xxx'
			// 	});
			// 	this.newsList = res.data.message;
			// }
			goDetail(id) {
				console.log(id,'id')
				uni.navigateTo({
					url: '/pages/news-detail/news-detail?id='+id
				});
			}
		},
		components: {
			"news-item": newsItem
		},
		onLoad() {
			// this.getNews();
		}
	}
</script>

<style lang="scss">
	.news {
		
	}
</style>
