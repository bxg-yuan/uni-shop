<template>
	<view class="contact">
		<image class="img" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fc-ssl.duitang.com%2Fuploads%2Fitem%2F201909%2F18%2F20190918132635_sEtH8.jpeg&refer=http%3A%2F%2Fc-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1637130377&t=871b64295765093be2e8632d9f96c20f"></image>
		<view class="info">
			<view @click="phone">联系电话：400-800-8888（点击拨打）</view>
			<view>联系地址：上海静安区</view>
		</view>
		<map class="map" :longitude="longitude" :scale="scale" :latitude="latitude" :markers="markers"></map>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 经纬度
				longitude: 121.452859,
				latitude: 31.229518,
				// 地址图标标记
				markers: [{
					longitude: 121.452859,
					latitude: 31.229518,
					iconPath: '../../static/position-fill.png',
					width: 30,
					height: 30
				}],
				// 地图缩放
				scale: 13
			}
		},
		methods: {
			// 拨打电话功能
			phone() {
				uni.makePhoneCall({
					phoneNumber: '400-800-8888'
				});
			}
		}
	}
</script>

<style lang="scss">
	.contact {
		.img {
			width: 750rpx;
			height: 320rpx;
		}
	}
	.info {
		padding: 10rpx 20rpx;
		font-size: 30rpx;
		view {
			line-height: 80rpx;
			border-bottom: 1px solid #eee;
		}
	}
	.map {
		width: 750rpx;
		height: 750rpx;
	}
</style>
