<template>
	<view>
		<view class="news_item" @click="navigator(item.id)" v-for="item in list" :key="item.id">
			<image :src="item.img_url"/>
			<view class="right_side">
				<view class="tit">
					{{item.title}}
				</view>
				<view class="info">
					<text>发表时间：{{item.add_time|formatDate}}</text>
					<text>浏览次数：{{item.click}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: ['list'],
		methods: {
			navigator(id){
				this.$emit('itemClick',id)
			}
		}
	}
</script>

<style lang="scss">
	.news_item {
		display: flex;
		padding: 10rpx 20rpx;
		border-bottom: 1px solid $idol-color;
		image {
			min-width: 200rpx;
			max-width: 200rpx;
			height: 150rpx;
		}
		.right_side {
			margin-left: 15rpx;
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			.tit {
				font-size: 33rpx;
			}
			.info {
				font-size: 24rpx;
				text:nth-child(2) {
					margin-left: 30rpx;
				}
			}
		}
	}
</style>
