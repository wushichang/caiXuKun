<template>
	<view>
		<view class="concernTop">
			<view class="iconfont iconcamera1">
				<text>随拍</text>
			</view>
			<view class="middle">
				<navigator :class="{'tabClicked': !tabStatus}" open-type="switchTab" url="../concern/concern">关注</navigator>
				<navigator :class="{'tabClicked': tabStatus}" open-type="switchTab" url="../friend/friend">好友</navigator>
			</view>
		</view>
		<view class="ground"></view>
	</view>
</template>

<script>
	export default{
		props: ['page'],
		data(){
			return {
				
			}
		},
		computed: {
			tabStatus(){
				return this.page === 'friend';
			}
		}
	}
</script>
<style>
	.concernTop {
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
	
	.ground {
		height: 72px;
		width: 100%;
	}
	
	.iconcamera1 {
		width: 24%;
		text-align: center;
		color: #FFFFFF;
		position: absolute;
		left: 0;
		top: 0;
	}
	
	.iconcamera1>text {
		margin-left: 8px;
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
	
	.tabClicked {
		border-bottom: 2px solid #F0AD4E;
	}
	
</style>
