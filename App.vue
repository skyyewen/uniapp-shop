<script>
	// import { mapGetters } from 'vuex'

	export default {
		onLaunch: function() {
			console.warn('当前组件仅支持 uni_modules 目录结构 ，请升级 HBuilderX 到 3.1.0 版本以上！')
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
			// this.setBadge()

		},
		onHide: function() {
			console.log('App Hide')
		},
		// computed: {
		// ...mapGetters('m_cart', ['total']),
		// },		// methods: {
		// 	setBadge() {
		// 	// 调用 uni.setTabBarBadge() 方法，为购物车设置右上角的徽标
		// 		uni.setTabBarBadge({
		// 			index: 2,
		// 			text: this.total + '', // 注意：text 的值必须是字符串，不能是数字
		// 		})
		// 	},
		// }		
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	@import '@/uni_modules/uni-scss/index.scss';
	/* #ifndef APP-NVUE */
	@import '@/static/customicons.css';
	// 设置整个项目的背景色
	page {
		background-color: #f5f5f5;
	}

	/* #endif */
	.example-info {
		font-size: 14px;
		color: #333;
		padding: 10px;
	}
</style>
