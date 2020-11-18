<template>
	<view class="news">
		<top-of-news></top-of-news>
		<news-content></news-content>
		<tab></tab>
	</view>
</template>

<script>
	import tab from '../../component/tab.vue';
	import topOfNews from '../../component/topOfNews.vue';
	import newsContent from '../../component/newsContent.vue';
	
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		components: {
			tab,
			topOfNews,
			newsContent
		}
	}
</script>

<style>
	.news {
		height: 100%;
		color: #FFFFFF;
		background-color: #000000;
	}
</style>
