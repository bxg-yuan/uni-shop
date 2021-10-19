<template>
	<view class="home">
		<!-- 轮播图 -->
		<swiper indicator-dots circular>
			<swiper-item v-for="(item,index) in swipers" :key="item.id">
				<image :src="item.img"></image>
			</swiper-item>
		</swiper>
		<!-- 导航区域 -->
		<view class="nav">
			<view class="nav_item" v-for="(item,index) in navs" :key="index" @click="navItemClick(item.path)">
				<view :class="item.icon"></view>
				<text>{{item.title}}</text>
			</view>
		</view>
		<!-- 爱豆明信片 -->
		<view class="hot_idol">
			<view class="tit">爱豆明信片</view>
			<goods-list :list="list" @goodsItemClick="goGoodsDetail"/>
		</view>
	</view>
</template>

<script>
	import CONFIG from '../../config/aiol_list.js';
	import GOODLIST from '../../config/goods.js';
	import goodsList from '../../components/goods-list/goods-list.vue';
	
	export default {
		data() {
			return {
				swipers: CONFIG.swipersList,
				idols: [],
				list: GOODLIST.list,
				navs: CONFIG.navs
			}
		},
		onLoad() {
			// 接口获取轮播图的写法
			// this.getSwipers();
		},
		components: {
			"goods-list": goodsList
		},
		methods: {
			// 接口获取轮播图的写法（这里我自己模拟的数据，所以就不调用接口了，只要知道写法就可以了）
			// 获取轮播图的数据
			//  async getSwipers() {
			// 	const res = await this.$myRequest({
			// 		url: '/api/getlunbo'
			// 	});
			// 	this.swipers = res.data.message;
			// }
			navItemClick(url){
				uni.navigateTo({
					url
				})
				console.log(url)
			},
			goGoodsDetail(id) {
				uni.navigateTo({
					url: '/pages/goods-detail/goods-detail?id='+id
				});
			}
		}
	}
</script>

<style lang="scss">
	.home {
		swiper {
			width: 750rpx;
			height: 380rpx;
			image {
				height: 100%;
				width: 100%;
			}
		}
		.nav {
			display: flex;
			.nav_item {
				width: 25%;
				text-align: center;
				view {
					width: 120rpx;
					height: 120rpx;
					background-color: $idol-color;
					border-radius: 60rpx;
					margin: 10px auto;
					line-height: 120rpx;
					color: #fff;
					font-size: 60rpx;
				}
				text {
					font-size: 30rpx;
				}
			}
		}
		.hot_idol {
			background: #eee;
			overflow: hidden;
			margin-top: 10px;
			.tit {
				height: 50px;
				line-height: 50px;
				color: $idol-color;
				text-align: center;
				letter-spacing: 20px;
				background: #fff;
				margin: 7px 0;
			}
			
		}
	}
</style>
