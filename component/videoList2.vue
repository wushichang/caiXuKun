<template>
	<view class="videoList2">
		<view class="item" v-for="(item,index) in 3" :key="index">
			<video 
			:src="'http://192.168.147.1:8080/video/'+(index+1)+'.mp4'" 
			objectFit="cover" 
			class="video" 
			:controls="true"></video>
			<view class="iconfont iconxihuan">
				123
			</view>
		</view>
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
	.videoList2{
		padding-bottom: 64px;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	
	.item {
		position: relative;
		width: 33.33%;
	}
	
	.video {
		width: 100%;
	}
	
	.iconxihuan {
		font-size: 15px;
		color: #FFFFFF;
		position: absolute;
		bottom: 8px;
		left: 8px;
	}
	
</style>
