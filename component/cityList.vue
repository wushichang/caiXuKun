<template>
	<scroll-view class="scrollView" scroll-y="true" :scroll-into-view="srollIntoView">
		<view class="cityList">
			<view class="currentCity">
				<view class="cityTitle">
					<icon class="iconfont icondingwei"></icon>
					<text>当前城市</text>
				</view>
				<view class="cityName">{{cityName}}</view>
			</view>
			
			<view class="currentCity ">
				<view class="cityTitle">
					<text>热门城市</text>
				</view>
				<view class="hotCities">
					<view class="hotCity" v-for="(item,index) in 12" :key="index">热点城市{{index+1}}</view>
				</view>
			</view>
			
			<view>
				<view v-for="item in cities" :key="item.initial">
					<view class="initial" :id="item.initial">{{item.initial}}</view>
					<view
					 class="cityItem"
					  v-for="(city,index) in item.list"
					   :key="index"
					   @click="chooseCity(city.name)">
					   {{city.name}}</view> 
				</view> 
			</view>
			
			
		</view>
	</scroll-view>
</template>

<script>
	
	export default{
		props: ['cities','initial'],
		data(){
			return {
				cityName: '长沙',
				srollIntoView: ''
			}
		},
		watch:{
			initial(newInitial){
				console.log('newInitial',newInitial);
				this.srollIntoView = newInitial;
			}
		},
		methods:{
			chooseCity(e){
				uni.setStorage({
					key: 'cityName',
					data: e,
					success: (res) => {
						this.cityName = e ;
						uni.navigateBack();
					}
				});
			}
				
		},
		created() {
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
	.scrollView {
		height: 100%;
	}
	
	.cityList {
		color: #FFFFFF;
		font-size: 14px;
	}
	
	.currentCity {
		margin-top: 15px;
		padding-bottom: 15px;
		background-color: #222222;
	}
	
	.cityTitle {
		height: 40px;
		line-height: 40px;
	}
	
	.icondingwei {
		color: #007AFF;
		font-size: 13px;
	}
	
	.cityName {
		font-size: 14px;
		height: 30px;
		line-height: 30px;
	}
	
	.hotCities {
		width: 90%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 12px;
		flex-wrap: wrap;
	}
	
	.hotCity {
		width: 32.5%;
		text-align: center;
		line-height: 28px;
		background-color: #333333;
		margin-bottom: 10px;
	}
	
	.initial {
		line-height: 40px;
	}
	
	.cityItem {
		line-height: 30px;
		background-color: #222222;
		padding-left: 2px;
	}
	
	
	
</style>
