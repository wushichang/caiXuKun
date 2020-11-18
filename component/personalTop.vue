<template>
	<view class="personal-top">
		<view class="img-box">
			<image src="../static/img/background.jpg" class="img" mode="aspectFill"></image>
		</view>

		<view class="information">
			<view class="head">
				<image src="../static/img/haha.jpg" class="head-img"></image>
			</view>
			<view class="information-tools">
				<view class="editInformation">编辑资料</view>
			</view>
		</view>

		<view class="information-detail">
			<view class="name">恩克</view>
			<view class="interval">抖音号：666666</view>
			<view class="line"></view>
			<view class="interval">欢迎大家来我家喝酒吃肉</view>
			<view class="interval">
				<text class="label">草原</text>
				<text class="label">内蒙古</text>
			</view>
			<view class="interval">
				<text class="number">666</text>
				<text class="category">点赞</text>
				<text class="number">777</text>
				<text class="category">关注</text>
				<text class="number">888</text>
				<text class="category">喜欢</text>
			</view>

			<view class="iconfont iconxiangji">
				添加随拍
			</view>

			<view class="tabs">
				<view :class="{tabChoosed: production}" @click="switchTab('production')">作品</view>
				<view :class="{tabChoosed: dynamicState}" @click="switchTab('dynamicState')">动态</view>
				<view :class="{tabChoosed: enjoy}" @click="switchTab('enjoy')">喜欢</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default{
		data(){
			return {
				production: true,
				dynamicState: false,
				enjoy: false,
				choosedTabValue: 'production'
			}
		},
		methods: {
			switchTab(res){
				switch(res){
					case 'production':
						this.production = true;
						this.choosedTabValue = 'production';
						this.dynamicState = false;
						this.enjoy = false;
					break;
					case 'dynamicState':
						this.production = false;
						this.dynamicState = true;
						this.choosedTabValue = 'dynamicState';
						this.enjoy = false;
					break;
					case 'enjoy':
						this.production = false;
						this.dynamicState = false;
						this.enjoy = true;
						this.choosedTabValue = 'enjoy';
					break;
				}
			}
		},
		watch: {
			choosedTabValue(tabValue){
				// console.log('tabValue',tabValue);
				this.$emit('tabValueChange',tabValue);
			}
		}
	}
</script>

<style>
	.personal-top {
		color: #FFFFFF;
		font-size: 15px;
	}

	.img-box {
		padding: 0 1px;
	}


	.img {
		width: 100%;
		height: 120px;
	}

	.head {
		position: relative;
	}

	.head-img {
		position: absolute;
		top: -48px;
		left: 16px;
		width: 64px;
		height: 64px;
		border-radius: 50%;
		border: 4px solid #000000;
	}

	.information {
		display: flex;
		align-items: center;
	}

	.information-tools {
		align-self: flex-start;
		margin: 0 0 8px 120px;
	}

	.editInformation {
		background-color: #333333;
		line-height: 40px;
		line-height: 40px;
		width: 120px;
		text-align: center;
		border-radius: 4px;
	}

	.information-detail {
		padding: 0 16px;
	}

	.name {
		font-size: 20px;
	}

	.line {
		border-top: 1px solid #222222;
	}

	.interval {
		line-height: 32px;
	}

	.label {
		font-size: 10px;
		display: inline-block;
		line-height: 20px;
		padding: 0px 8px;
		background-color: #333333;
		border-radius: 5%;
		/* 此处还有更好的方法 */
		margin-right: 10px;
	}

	.category {
		color: #999999;
		margin-right: 8px;
	}

	.iconxiangji {
		line-height: 40px;
		background-color: #333333;
		border-radius: 4px;
		text-align: center;
		margin-top: 4px;
	}
	
	.tabs {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	
	.tabs>view {
		color: #999999;
		line-height: 32px;
		width: 33%;
		text-align: center;
	}
	
	.tabChoosed {
		border-bottom: 2px solid #F0AD4E;
	}
	
	
	
</style>
