<template>
	<view class="concern">
		<concern-top :page="page"></concern-top>
		<concern-list :page="page"></concern-list>
		<tab></tab>
	</view>
</template>

<script>
	import concernTop from '../../component/concernTop.vue';
	import concernList from '../../component/concernList.vue';
	import tab from '../../component/tab.vue';
	
	export default {
		data() {
			return {
				page: 'concern'
			}
		},
		methods: {
			
		},
		components: {
			concernTop,
			concernList,
			tab
		}
	}
</script>

<style>
	page {
		background-color: #000000;
	}
	
	.concern {
		height: 100%;
	}
</style>
