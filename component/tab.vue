<template>
		<view class="tab">
			<navigator class="tab-box" open-type="switchTab" url="../index/index">首页</navigator>
			<navigator class="tab-box" open-type="switchTab" url="../concern/concern">关注</navigator>
			<view class="tab-box">
				<view class="iconfont icontianjia"></view>
			</view>
			<navigator class="tab-box" open-type="switchTab" url="../news/news">消息</navigator>
			<navigator class="tab-box" open-type="switchTab" url="../personal/personal">我</navigator>
		</view>
</template>

<script>
</script>

<style>
	.tab{
		position: fixed;
		left: 0;
		bottom: 0;
		width: 100%;
		display: flex;
		justify-content: space-around;
		align-items: center;
		/* background-color: #000000; */
		z-index: 1;
	}
	
	.tab-box{
		width: 20%;
		color: #FFFFFF;
		line-height: 50px;
		text-align: center;
	}
	
	.icontianjia {
		width: 60%;
		height: 30px;
		line-height: 30px;
		margin: 10px 20%;
		background-color: #FFFFFF;
		color: #000000;
		border-radius: 5px;
	}
	
</style>
