<template>
	<view class="personal">
		<personal-top @tabValueChange="tabValueChange"></personal-top>
		<view v-show="tabValue === 'production'">
			<video-list2></video-list2>
		</view>
		<view v-show="tabValue === 'dynamicState'" class="concernList">
			<concern-list></concern-list>
		</view>
		<view v-show="tabValue === 'enjoy'">
			<video-list2></video-list2>
		</view>
		 
		<tab></tab>
	</view>
</template>

<script>
	import tab from '../../component/tab.vue';
	import personalTop from '../../component/personalTop.vue';
	import videoList2 from '../../component/videoList2.vue';
	import concernList from '../../component/concernList.vue';
	export default {
		data() {
			return {
				tabValue: 'production'
			}
		},
		methods: {
			tabValueChange(tabValue){
				this.tabValue = tabValue;
			}
		},
		components: {
			tab,
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
	}
	.concernList {
		height: 100%;
	}
</style>
