<template>
	<view class="descriptionContainer">
		<view class="author">@{{video.author}}</view>
		<view class="title">{{video.title}}</view>
		<view class="music">
			<view>欧巴，擦浪黑油。哈哈哈哈哈哈哈。</view>
		</view>
	</view>
</template>

<script>
	export default{
		props: ['video'],
		data() {
			return{
				
			}
		}
	}
</script>

<style>
	.descriptionContainer {
		width: 120px;
		position: absolute;
		bottom: 50px;
		left: 10px;
		color: #FFFFFF;
		font-size: 15px;
	}
	
	.author {
		line-height: 30px;
	}
	
	.title {
		font-size: 12px;
		line-height: 15px;
	}
	
	.music {
		font-size: 12px;
		line-height: 30px;
		white-space: nowrap;
		width: 100px;
		overflow: hidden;
	}
	
	.music>view {
		animation: move 4s linear .25s infinite;
		width: 150px;
	}
	
	/* 文字移动动画  也可以用百分比 */
	@keyframes move{
		from{
			transform: translateX(70%);
		}
		to{
			transform: translateX(-70%);
		}
	}
	
</style>
