<template>
	<view>
		<goods-list @goodsItemClick="goGoodsDetail" :list="list" class="goods-list"/>
		<view class="isOver" v-if="flag">-----我是有底线的-----</view>
	</view>
</template>

<script>
	import goodsList from '../../components/goods-list/goods-list.vue';
	import CONFIG from '../../config/goods.js';
	
	export default {
		data() {
			return {
				list: CONFIG.list,
				flag: false,
				pageindex: 1
			}
		},
		components: {
			"goods-list": goodsList
		},
		methods: {
			// 有接口的情况下获取商品列表数据
			// async getGoodsList(callBack) {
			// 	const res = await this.$myRequest({
			// 		url: '/api/getgoods?pageindex='+this.pageindex
			// 	});
			// 	this.list = [...this.liat,...res.data.message];
			// 	callBack&&callBack();
			// }
			goGoodsDetail(id) {
				uni.navigateTo({
					url: '/pages/goods-detail/goods-detail?id='+id
				});
			}
		},
		onLoad() {
			// this.getGoodsList();
		},
		// 页面滚动到底部的事件
		onReachBottom() {
			// 有接口的情况下，下拉到最后一页显示‘我是有底线的’
			// if (this.list.length<this.pageindex*10) return this.flag=true;
			// this.pageindex++;
			// this.getGoodsList();
			
			// 无接口的情况下自己模拟的数据获取列表数据
			this.list = [...this.list,...CONFIG.listPage2];
		},
		onPullDownRefresh() {
			// 有接口的情况下下拉刷新
			// this.pageindex = 1;
			// this.list = [];
			// this.flag = false;
			// setTimeout(()=>{
			// 	this.getGoodsList(()=>{
			// 		uni.stopPullDownRefresh();
			// 	});
			// },1000)
			
			// 无接口自己模拟数据的情况下下拉刷新
			this.list = [];
			this.flag = false;
			setTimeout(()=>{
				this.list = CONFIG.list;
				uni.stopPullDownRefresh();
			},1000)
		},
	}
</script>

<style lang="scss">
	.goods-list {
		background: #eee;
	}
	.isOver {
		width: 100%;
		height: 50px;
		line-height: 50px;
		text-align: center;
		font-size: 28rpx;
	}
</style>
