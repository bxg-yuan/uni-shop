<template>
	<view class="pics">
		<scroll-view class="left" scroll-y>
			<view
			@click="sideClickHandle(index,item.id)"
			:class="active===index?'active':''"
			v-for="(item,index) in sideList"
			:key="item.id"
			>{{item.title}}</view>
		</scroll-view>
		<scroll-view class="right" scroll-y>
			<view class="item" v-for="(item,index) in secondData" :key="index">
				<image @click="previewImg(item.img_url)" :src="item.img_url"></image>
				<text>{{item.title}}</text>
			</view>
			<text v-if="secondData.length===0">暂无数据</text>
		</scroll-view>
	</view>
</template>

<script>
	import CONFIG from '../../config/pics.js';
	
	export default {
		data() {
			return {
				sideList: CONFIG.sideList,
				active: 0,
				secondData: []
			}
		},
		onLoad() {
			this.secondData = CONFIG.rightList[0].message;
		},
		methods: {
			sideClickHandle(index,id) {
				this.secondData = [];
				this.active = index;
				this.secondData = CONFIG.rightList[index].message;
			},
			previewImg(current) {
				const urls = this.secondData.map(item=>{
					return item.img_url
				});
				// 图片放大预览
				uni.previewImage({
					current,//显示点击的当前图片
					urls
				});
			}
		}
	}
</script>

<style lang="scss">
	page {
		height: 100%;
	}
	.pics {
		height: 100%;
		display: flex;
		.left {
			width: 200rpx;
			height: 100%;
			border-right: 1px solid #eee;
			view {
				height: 60px;
				line-height: 60px;
				color: #333;
				text-align: center;
				font-size: 30rpx;
				border-top: 1px solid #eee;
			}
			.active {
				background: $idol-color;
				color: #fff;
			}
		}
		.right{
			height: 100%;
			width: 520rpx;
			margin: 10rpx auto;
			.item {
				image {
					width: 520rpx;
					height: 520rpx;
					border-radius: 5px;
				}
				text {
					font-size: 30rpx;
					line-height: 60rpx;
				}
			}
		}
	}
</style>
