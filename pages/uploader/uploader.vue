<template>
	<view class="personal">
		<icon class="iconfont iconfanhui" @click="navigateBack"></icon>
		<personal-top :page='page' @tabValueChange="tabValueChange"></personal-top>
		<view v-show="tabValue === 'production'">
			<video-list2></video-list2>
		</view>
		<view v-show="tabValue === 'dynamicState'" class="concernList">
			<concern-list></concern-list>
		</view>
		<view v-show="tabValue === 'enjoy'">
			<video-list2></video-list2>
		</view>
	</view>
</template>

<script>
	import personalTop from '../../component/personalTop.vue';
	import videoList2 from '../../component/videoList2.vue';
	import concernList from '../../component/concernList.vue';
	export default {
		data() {
			return {
				tabValue: 'production',
				page: 'uploader'
			}
		},
		methods: {
			tabValueChange(tabValue){
				this.tabValue = tabValue;
			},
			navigateBack(){
				uni.navigateBack();
			}
		},
		components: {
			personalTop,
			videoList2,
			concernList
		}
		
	}
</script>

<style>
	page {
		background-color: #000000;
	}
	
	.personal {
		height: 100%;
		position: relative;
	}
	
	.concernList {
		height: 100%;
	}
	
	.iconfanhui {
		color: #FFFFFF;
		position: absolute;
		top: 24px;
		left: 12px;
	}
	
	
</style>
