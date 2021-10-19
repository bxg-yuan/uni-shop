<template>
	<view class="idol_list">
		<view class="idol_item" v-for="(item,index) in list" :key="index" @click="navigator(item.id)">
			<image :src="item.img_url"></image>
			<view class="price">
				<text>￥{{item.sell_price}}</text>
				<text>￥{{item.market_price}}</text>
			</view>
			<view class="name">
				{{item.title}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: ['list'],
		data () {
			return {
				
			}
		},
		methods: {
			navigator(id) {
				this.$emit('goodsItemClick',id)
			}
		}
	}
</script>

<style lang="scss">
	.idol_list {
		padding: 0 15rpx;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		.idol_item {
			background: #fff;
			width: 355rpx;
			margin: 10rpx 0;
			padding: 15rpx;
			box-sizing: border-box;
			image {
				width: 80%;
				height: 150px;
				display: block;
				margin: 0 auto;
			}
			.price {
				color: $idol-color;
				font-size: 36rpx;
				margin: 20rpx 0 5rpx 0;
				text:nth-child(2) {
					color: #ccc;
					font-size: 28rpx;
					margin-left: 17rpx;
					text-decoration: line-through;
				}
			}
			.name {
				font-size: 28rpx;
				line-height: 50rpx;
				padding: 10rpx 0 15rpx 0;
			}
		}
	}
</style>
