<template>
	<view class="cityContent">
		<view class="position">
			<view>
				<view class="iconfont icondingwei">自动定位：{{cityName}}</view>
			</view>
			<navigator open-type="navigate" url="../changeCity/changeCity" class="changeCity">
				切换<text class="iconfont iconjinru"></text>
			</navigator>
		</view>
		<view class="videoList">
			<view class="videoItem">
				<view class="videoBox">
					<video
					class="video" 
					src="http://192.168.147.1:8080/video/1.mp4"
					objectFit="fill">
					</video>
				</view>
				<view class="imgBox">
					<image src="../static/img/haha.jpg" class="img"></image>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		props: ['cityName'],
		data(){
			return{
				
			}
		}
	}
</script>

<style>
	.cityContent {
		padding-top: 64px;
		color: #aaaaaa;
		font-size: 12px;
	}
	
	.position {
		padding: 0 15px;
		display: flex;
		justify-content: space-between;
	}
	
	.icondingwei {
		font-size: 12px;
	}
	
	.changeCity {
		display: flex;
	}
	
	.videoList {
		padding: 12px 4px;
	}
	
	.videoItem {
		width: 49.7%;
		height: 240px;
		float: left;
		position: relative;
	}
	
	.videoItem:nth-child(2n){
		margin-right: 2px;
	}
	
	
	.video {
		width: 100%;
		height: 240px;
	}
	
	.imgBox {
		position: absolute;
		right: 10px;
		bottom: 12px;
	}
	
	.img {
		width: 36px;
		height: 36px;
		border-radius: 50%;
	}
	
	
	
</style>
