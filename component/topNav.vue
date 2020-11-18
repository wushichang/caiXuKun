<template>
	<view class="topNav">
		<view class="iconfont iconsousuo"></view>
		<view class="middle">
			<navigator open-type="switchTab" url="../index/index">推荐</navigator>
			<navigator open-type="navigate" url="../city/city">同城</navigator>
		</view>
	</view>
</template>

<script>
</script>
<style>
	.topNav {
		width: 100%;
		/* background-color: #000000; */
		position: fixed;
		top: 25px;
		left: 0;
		height: 35px;
		line-height: 35px;
		/* 担心被视频组件覆盖 */
		z-index: 1;
	}
	
	.iconsousuo {
		width: 20%;
		text-align: center;
		color: #FFFFFF;
		font-size: 20px;
		position: absolute;
		left: 0;
		top: 0;
	}
	
	.middle {
		text-align: center;
		color: #FFFFFF;
		display: flex;
		justify-content: center;
	}
	
	.middle>navigator {
		padding: 0 10px;
	}
	
</style>
