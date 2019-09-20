<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
			let isLogin = uni.getStorageSync('login');
			if(isLogin) {
				uni.navigateTo({url: '/pages/center/mine/index'})
			} else {
				uni.navigateTo({url: '/pages/login/index'})
			}
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
</style>
