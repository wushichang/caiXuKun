<template>
	<view class="city">
		<top-nav></top-nav>
		<city-content :cityName="cityName"></city-content>
		<tab></tab>
	</view>
</template>

<script>
	import topNav from '../../component/topNav.vue';
	import cityContent from '../../component/cityContent.vue';
	import tab from '../../component/tab.vue';
	export default {
		data() {
			return {
				cityName: '长沙'
			}
		},
		methods: {
			
		},
		components: {
			topNav,
			cityContent,
			tab
		},
		onShow() {
			uni.getStorage({
				key: 'cityName',
				success: (res) => {
					this.cityName = res.data;
				}
			})
		}
	}
</script>

<style>
	.city {
		background-color: #000000;
		width: 100%;
		height: 100%;
	}
</style>
