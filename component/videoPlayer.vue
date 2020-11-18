<template>
	<view>
		<view>
			
			<video 
			id="myVideo" 
			class="video" 
			:src="'http://192.168.147.1:8080/video/'+video.src" 
			:loop="true" 
			:controls="false" 
			:autoplay="index === 0"
			@error="error"
			@click="videoClick">
			</video>
			
		</view>
	</view>
</template>

<script>
	var timer = null;
	export default {
		props: ['video','index'],
		data() {
			return {
				playState: false,
				doubleClick: false
			};
		},
		computed: {
			
		},
		methods: {
			videoClick(){
				clearTimeout(timer);
				this.doubleClick = !this.doubleClick;
				timer = setTimeout(()=>{
					if(this.doubleClick){
						this.playState?this.stop():this.goAhead();
						this.doubleClick = false;
					}else{
						this.$emit('doubleClick');
					}
				},200)
			},
			error(erro){ 
				console.log('视频播放错误',erro);
			},
			play(){
				if(!this.playState){
					this.videoContext.seek(0);
					this.videoContext.play();
					this.playState = true;
				}
			},
			stop(){
				//这个if判断我感觉也是多余的
				if(this.playState){
					this.videoContext.pause();
					this.playState = false;
				}
			},
			goAhead(){
				if(!this.playState){
					this.videoContext.play();
					this.playState = true;
				}
			}
		},
		created() {
			this.playState = this.index === 0;
		},
		onReady() {
			this.videoContext = uni.createVideoContext('myVideo',this);
		},
		onLoad() {
			
		}
	}
</script>

<style>
	.video {
		width: 100%;
		height: calc(100vh);
	}
</style>
