<template>
	<view class="content">
		<!-- 顶部导航栏 -->
		<top-nav></top-nav>
		
		<!-- 视频组件 -->
		<video-list :videos="videos"></video-list>
		
		<!-- 底部导航栏 -->
		<tab></tab>
		
	</view>
	
	
</template>

<script>
	import tab from '../../component/tab.vue';
	import videoList from '../../component/videoList.vue';
	import topNav from '../../component/topNav.vue';
	export default {
		components: {
			tab,
			videoList,
			topNav
		},
		data() {
			return {
				videos: []
			}
		},
		onLoad() {
			// #ifndef MP-WEIXIN
				console.log('清除tab导航');
				uni.hideTabBar();
			// #endif
			this.videoList();//加载视频
		},
		methods: {
			videoList(){
				uni.request({
					url: 'http://localhost:8080/videoList',
					success: (res) => {
						// console.log('视频列表',res);
						this.videos = res.data;
					},
					fail: (error) => {
						console.log('视频列表请求失败',error);
					}
				})
			}
		}
	}
</script>

<style>
	.content {
		width: 100%;
		height: 100%;
		background-color: #000000;
	}
</style>
