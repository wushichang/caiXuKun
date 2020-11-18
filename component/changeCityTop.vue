<template>
	<view>
		<navigator class="top">
			<navigator open-type="navigateBack" url="../city/city" class="iconfont iconicon-"></navigator>
			<view class="changeText">切换城市</view>
		</navigator>
		<view class="space"></view>
	</view>
	
</template>

<script>
	export default{
		data(){
			return {
				
			}
		}
	}
</script>

<style>
	.top {
		height: 80px;
		width: 100%;
		text-align: center;
		color: #FFFFFF;
		background-color: #000000;
		position: fixed;
	}
	
	.space {
		height: 80px;
		width: 100%;
	}
	
	.iconicon- {
		line-height: 80px;
		color: #AAAAAA;
		position: absolute;
	}
	
	.changeText {
		line-height: 80px;
		/* 和默认图标的大小一样iconfont */
		font-size: 16px;
	}
	
	
	
</style>
