<template>
	<view class="tools">
		<view class="uploaderInfo">
			<image class="img headIcon" src="../static/img/haha.jpg" @click="goUploaderPage"></image>
			<view class="iconfont icontianjia concern" @click="concern" v-show="!concernedState"></view>
		</view>
		<view class="iconfont iconxihuan operation" @click="giveLike" :style="likeStyle"></view>
		<view class="number">{{video.loveNumber}}</view>
		<view class="iconfont icontubiaozhizuo- operation"></view>
		<view class="number">{{video.commentNumber}}</view>
		<view class="iconfont iconzhuanfa operation"></view> 
		<view class="number">{{video.shareNumber}}</view>
		<view class="disc">
			<image class="share" src="../static/img/share.png"></image>
		</view>
	</view> 
</template>

<script>
	export default{
		props: ['video'],
		data(){
			return {
				concernedState: false,
				likeStyle: ''//喜欢的样式
			}
		},
		methods:{
			concern(){
				this.concernedState = true;
			},
			giveLike(){
				this.likeStyle = this.likeStyle === ''?'color:#ff0000;':'';
			},
			doubleClick(){
				this.likeStyle = 'color:#ff0000';
			},
			goUploaderPage(){
				uni.navigateTo({
					url: '../uploader/uploader'
				})
			}
		}
	}
</script>

<style>
	.tools {
		width: 50px;
		text-align: center;
		color: #FFFFFF;
		font-size: 15px;
		position: absolute;
		right: 10px;
		bottom: 50px;
	}
	
	.uploaderInfo {
		position: relative;
	}
	
	.img {
		width: 36px;
		height: 36px;
		border-radius: 50%; 
	}
	
	.headIcon {
		border: 1px solid #FFFFFF;
	}
	
	.concern {
		background-color: #ff0000;
		color: #FFFFFF;
		width: 16px;
		height: 16px;
		border-radius: 50%;
		position: absolute;
		left: 17px;
		bottom: -5px;
	}
	
	.operation {
		margin-top: 15px;
		font-size: 20px;
	}
	
	.number {
		font-size: 10px;
	}
	
	.disc {
		width: 38px;
		height: 38px;
		margin: 0 auto;
		margin-top: 15px;
		animation: spin 2s linear 0.25s infinite;
	}
	
	.share {
		width: 100%;
		height: 100%;
		border-radius: 50%;
	}
	
	/* 碟片选装动画 */
	@keyframes spin{
		from{
			transform: rotate(0);
		}
		to{
			transform: rotate(360deg);
		}
	}
	
</style>
