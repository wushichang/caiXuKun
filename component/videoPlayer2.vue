<template>
	<view>
		<video
		id="myVideo" 
		class="video" 
		:src="'http://192.168.147.1:8080/video/'+videoOptions.src" 
		:loop="true" 
		:controls="false"
		objectFit="cover"
		:autoplay="index === 0"
		@click="blowUp(index)">
			<icon class="iconfont iconicon_play" @click.stop="click"></icon>
		</video>
	</view>
</template>

<script>
	export default{
		props: ['videoOptions','index'],
		data(){
			return {
				playStatus: false
			}
		},
		methods: {
			play(){
				if(!this.playStatus){
					this.videoContext.play();
					this.playStatus = true;
				}
			},
			pause(){
				if(this.playStatus){
					this.videoContext.pause();
					this.playStatus = false;
				}
			},
			click(){
				if(this.playStatus){
					this.videoContext.pause();
					this.playStatus = false;
				}else{
					this.videoContext.play();
					this.playStatus = true;
				}
			},
			blowUp(index){
				uni.navigateTo({
					url: '../videoSwiper/videoSwiper?current='+index
				})
			}
		},
		onReady() {
			this.videoContext = uni.createVideoContext("myVideo",this);
			if(this.index === 0){
				this.playStatus = true;
			}
		}
		
	}
</script>

<style>
	.video {
		width: 80%;
	}
	
	.iconicon_play {
		color: #FFFFFF;
		font-size: 20px;
		position: absolute;
		bottom: 10px;
		right: 10px;
	}
</style>
