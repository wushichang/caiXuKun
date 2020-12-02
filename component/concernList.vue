<template>
	<view class="concernList">
		<scroll-view scroll-y="true" @scroll="scroll" class="scrollView">
			<view class="concernItem" v-for="(item,index) in list" :key = 'item.id'>
				<view class="top">
					<view class="img-box">
						<image src="../static/img/haha.jpg" class="img"></image>
						<view class="author">{{item.author}}</view>
					</view>
					<view class="share iconfont iconshenglve"></view>
				</view>
				<view class="title">
					{{item.title}}
				</view>
				<view class="video-box">
					<video-player2 :videoOptions = "item" :index="page?index:index+1" ref="videoPlayers" ></video-player2>
					<view class="music-box">
						<view class="music">如果我是DJ你会爱我吗</view>
					</view>
				</view>
				<view class="box">
					<view class="date">
						11-13
					</view>
					<view class="operators box">
						<view class="iconfont iconzhuanfa">
							<text>转发</text>
						</view>
						<view class="iconfont icontubiaozhizuo-">
							<text>评论</text>
						</view>
						<view class="iconfont iconxihuan">
							<text>喜欢</text>
						</view>
					</view>
				</view>
				<view class="comment">
					<view class="sum">4.4w条评论</view>
					<label class="iconfont iconbianji-01">
						<input class="mywords" placeholder="说点什么..."/>
					</label>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import videoPlayer2 from './videoPlayer2.vue';
	
	export default{
		props: ['page'],
		data(){
			return {
				list: [],
				videoIndex: 0
			}
		},
		methods:{
			videoList(){
				uni.request({
					url:'http://192.168.147.1:8080/videoList',
					success: (res) => {
						this.list = this.page=='friend'? res.data.slice(3):res.data.slice(0,3);
						// 把视频数据放到缓存中，给videoSwiper使用
						uni.setStorage({
							key: 'videoList',
							data: this.list
						})
					}
				})
			},
			scroll(e){
				clearInterval(timer);
				var timer = setTimeout(()=>{
					this.videoIndex = Math.floor(e.detail.scrollTop/225);
				},100)
			}
		},
		created() {
			this.videoList();
		},
		components: {
			videoPlayer2
		},
		watch: {
			videoIndex(videoIndex){
				this.$refs.videoPlayers[videoIndex].play();
				if(videoIndex === 0){
					this.$refs.videoPlayers[videoIndex+1].pause();
				}else if(videoIndex === this.$refs.videoPlayers.length-1){
					this.$refs.videoPlayers[videoIndex-1].pause();
				}else{
					this.$refs.videoPlayers[videoIndex+1].pause();
					this.$refs.videoPlayers[videoIndex-1].pause();
				}
			}
		}
	}
</script>

<style>
	.concernList {
		color: #FFFFFF;
		padding: 0 15px 60px 15px;
		height: 100%;
	}
	
	.scrollView {
		height: 100%;
		
	}
	
	.top {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	
	.img-box {
		display: flex;
		align-items: center;
	}
	
	.author {
		margin-left: 10px;
	}
	
	.img {
		width: 36px;
		height: 36px;
		border-radius: 50%;
	}
	
	.title {
		line-height: 48px;
	}
	
	.video-box {
		height: 256px;
	}
	
	
	
	.box {
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 12px;
	}
	
	.date {
		background-color: #AAAAAA;
		line-height: 15px;
		padding: 0px 8px;
	}
	
	.operators {
		width: 50%;
	}
	
	.operators>text {
		font-size: 12px;
	}
	
	.iconfont {
		font-size: 15px;
		word-break: keep-all;
	}
	
	.sum {
		font-size: 10px;
		line-height: 28px;
	}
	
	.iconbianji-01 {
		display: flex;
		align-items: center;
	}
	
	.music-box {
		width: 120px;
		font-size: 12px;
		overflow: hidden;
	}
	
	.music {
		width: 160px;
		animation: song 4s linear infinite;
	}
	
	@keyframes song{
		from{
			transform: translateX(80%);
		}
		to{
			transform: translateX(-80%);
		}
	}
	
</style>
