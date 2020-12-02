<template>
	<view class="videoSwiper">
		<view class="iconfont iconfanhui" @click="click"></view>
		<video-list :videos = 'list' :current = 'current'></video-list>
		<view class="tips">说两句撒</view>
	</view>
	
</template>

<script>
	import videoList from '../../component/videoList.vue';
	export default {
		props: ['current'],
		data() {
			return {
				list: []
			}
		},
		components: {
			videoList
		},
		methods: {
			click(){
				uni.navigateBack();
			}
		},
		created(){
			// 获取缓存中的视频信息
			uni.getStorage({
				key: 'videoList',
				success: (res)=>{
					this.list = res.data;
				}
			});
		}
	}
</script>

<style>
	.videoSwiper {
		height: 100%;
		position: relative;
	}
	
	.iconfanhui {
		position: absolute;
		z-index: 1;
		color: #ffffff;
		top: 24px;
		left: 12px;
	}
	
	.tips {
		position: absolute;
		z-index: 1;
		color: #444444;
		bottom: 24px;
		left: 12px;
	}
	
	
</style>
