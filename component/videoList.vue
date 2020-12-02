<template>
	<view>
		<view>
			<swiper class="swiper" vertical="true" @change="change" @touchstart="touchStart" @touchend="touchEnd" :current="current || 0">
				<swiper-item  v-for="(video,index) in videos" :key="video.id">
					<video-player ref="player" :video="video" @doubleClick = "doubleClick(index)" :index = "index" :current="current"></video-player>
					<video-desc :video="video"></video-desc>
					<tools ref="tools" :video="video"></tools>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import videoPlayer from './videoPlayer.vue';
	import videoDesc from './videoDesc.vue';
	import tools from './tools.vue';
	
	var swiperTimeout = null;//定时器
	
	export default {
		props: ['videos','current'],
		data(){
			return {
				startClientY: 0,
				endClientY: 0,
				page: 0
			}
		},
		methods: {
			change(e){
				// console.log('change',e);
				clearTimeout(swiperTimeout);//清除定时器
				this.page = e.detail.current;//不知道要他干什么
				setTimeout(()=>{
					if(this.startClientY > this.endClientY){
						this.$refs.player[e.detail.current].play();
						this.$refs.player[e.detail.current-1].stop();
					}else{
						this.$refs.player[e.detail.current].play();
						this.$refs.player[e.detail.current+1].stop();
					};
					//此处存在性有待考证
					this.startClientY = 0; 
					this.endClientY = 0; 
				},1);
				
			},
			touchStart(e){
				// console.log('touchStart',e);
				this.startClientY = e.changedTouches[0].clientY;
			},
			touchEnd(e){
				// console.log('touchEnd',e);
				this.endClientY = e.changedTouches[0].clientY;
			},
			doubleClick(index){
				this.$refs.tools[index].doubleClick();
			}
		},
		components: {
			videoPlayer,
			videoDesc,
			tools
		}
	}
</script>

<style>
	.swiper {
		width: 100%;
		height: calc(100vh);
	}
</style>
