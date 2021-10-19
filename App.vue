<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	@font-face {
	  font-family: "iconfont"; /* Project id 2870298 */
	  src: url('~@/static/font/iconfont.woff2?t=1634280884396') format('woff2'),
	       url('~@/static/font/iconfont.woff?t=1634280884396') format('woff'),
	       url('~@/static/font/iconfont.ttf?t=1634280884396') format('truetype');
	}
	
	.iconfont {
	  font-family: "iconfont" !important;
	  font-size: 16px;
	  font-style: normal;
	  -webkit-font-smoothing: antialiased;
	  -moz-osx-font-smoothing: grayscale;
	}
	
	.icon-camera-fill:before {
	  content: "\e77a";
	}
	
	.icon-pic-fill:before {
	  content: "\e788";
	}
	
	.icon-service-fill:before {
	  content: "\e78c";
	}
	
	.icon-trade-assurance-fill:before {
	  content: "\e790";
	}
	
	.icon-rejected-order-fill:before {
	  content: "\e79e";
	}
	.gomeImgLoad {
		width: 750rpx;
		height: auto;
	}
</style>
