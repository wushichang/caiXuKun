<template>
	<view class="changeCity">
		<change-city-top></change-city-top>
		<city-list :cities="cities" :initial='initial'></city-list>
		<alphabet :cities="cities" @clickInitial="clickInitial"></alphabet>
	</view>
</template>

<script>
	import changeCityTop from '../../component/changeCityTop.vue';
	import cityList from '../../component/cityList.vue';
	import alphabet from '../../component/alphabet.vue';
	
	const cities = require('../../static/json/city.json');
	
	export default {
		data() {
			return {
				cities: cities.city,
				initial: ''
			}
		},
		methods: {
			clickInitial(initial){
				this.initial = initial;
			}
		},
		components: {
			changeCityTop,
			cityList,
			alphabet
		}
		
	}
</script>

<style>
	.changeCity {
		background-color: #000000;
		width: 100%;
		height: 100%;
		padding: 0 12px;
	}
</style>
