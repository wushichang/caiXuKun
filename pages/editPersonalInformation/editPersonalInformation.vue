<template>
	<view class="personalInformation">
		<view class="head">
			<navigator class="iconfont iconfanhui" open-type="navigateBack" url="../personal/personal"></navigator>
			<text>编辑个人信息</text>
		</view>
		
		<view class="photo">
			<image class="img" :src="imgSrc" @click="changePhoto"></image>
			<view class="description">点击更换头像</view>
		</view>
		
		<view class="list">
			<view class="item">
				<view class="label">昵称</view>
				<navigator class="value" open-type="navigate" url="../changeName/changeName?category=name">
					{{userInfo.name}}
					<view class="iconfont iconjinru"></view>
				</navigator>
				
			</view>
			
			<view class="item">
				<view class="label">抖音号</view>
				<navigator class="value" open-type="navigate" url="../changeName/changeName?category=account">
					{{userInfo.account}}
					<view class="iconfont iconjinru"></view>
				</navigator>
			</view>
			
			<view class="item">
				<view class="label">简介</view>
				<navigator class="value" open-type="navigate" url="../changeName/changeName?category=introduction">
					{{userInfo.introduction}}
					<view class="iconfont iconjinru"></view>
				</navigator>
			</view>
			
			
			<picker @change="chooseSchool" :range="schoolList" :value="schoolListIndex">
				<view class="item">
					<view class="label">学校</view>
					<view class="value">
						{{schoolList[schoolListIndex] || '无'}}
						<view class="iconfont iconjinru"></view>
					</view>
				</view>
			</picker>
			
			<picker @change="chooseSex" :range="sexList" :value="sexListIndex">
				<view class="item">
					<view class="label">性别</view>
					<view class="value">
						{{sexList[sexListIndex]}}
						<view class="iconfont iconjinru"></view>
					</view>
				</view>
			</picker>
			
			
			<picker mode="date" @change="dateChange" :start="getDate('start')" :end="getDate('end')">
				<view class="item">
					<view class="label">生日</view>
					<view class="value">
						{{userInfo.birthDay || ''}}
						<view class="iconfont iconjinru"></view>
					</view>
				</view>
			</picker>
			
			<picker @change="regionChange" mode="region">
				<view class="item">
					<view class="label">地区</view>
					<view class="value">
						{{userInfo.region || '无'}}
						<view class="iconfont iconjinru"></view>
					</view>
				</view>
			</picker>
			
			
			
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgSrc: '../../static/img/haha.jpg',
				userInfo: {},
				schoolList: ['新东方','蓝翔','加里敦'],
				schoolListIndex: -1,
				sexList: ['男','女','不详'],
				sexListIndex: 0
			}
		},
		methods: {
			changePhoto(){
				uni.chooseImage({
					count: 1,
					success: (res) => {
						this.imgSrc = res.tempFilePaths[0];
					}
				})
			},
			chooseSchool(e){
				this.schoolListIndex = e.detail.value;
			},
			chooseSex(e){
				this.sexListIndex = e.detail.value;
			},
			setUserInfo(){
				uni.setStorage({
					key: 'userInfo',
					data: this.userInfo
				});
			},
			 getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
	
				if (type === 'start') {
					year = year - 100;
				} else if (type === 'end') {
					// year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
			
			dateChange(e){
				// 这里就不做监听了
				this.userInfo.birthDay = e.detail.value;
				this.setUserInfo();
			},
			
			regionChange(e){
				// 这里就不做监听了
				this.userInfo.region = e.detail.value[0];
				this.setUserInfo();
			}
			
		},
		watch: {
			schoolListIndex(newIndex){
				this.userInfo.school = this.schoolList[newIndex];
				this.setUserInfo();
			},
			sexListIndex(newIndex){
				this.userInfo.sex = this.sexList[newIndex];
				this.setUserInfo();
			}
		},
		onShow() {
			uni.getStorage({
				key: 'userInfo',
				success: (res) => {
					if(res.data)this.userInfo = res.data;
					this.schoolListIndex = this.schoolList.indexOf(this.userInfo.school);
					const index = this.sexList.indexOf(this.userInfo.sex);
					this.sexListIndex = index === -1 ?0:index;
				}
			});
		}
	}
</script>

<style>
	.personalInformation {
		height: 100%;
		background-color: #000000;
		color: #FFFFFF;
	}
	
	.head {
		padding-top: 28px;
		text-align: center;
		font-size: 16px;
		line-height: 20px;
	}
	
	.iconfanhui {
		float: left;
	}
	
	.photo {
		height: 120px;
		text-align: center;
		margin-top: 16px;
		display: flex;
		flex-direction: column;
		align-items: center;
		flex-direction: column;
		justify-content: center;
		border-top: 1px solid #222222;
		border-bottom: 1px solid #222222;
	}
	
	.img {
		width: 48px;
		height: 48px;
		border-radius: 50%;
	}
	
	.description {
		color: #999999;
		font-size: 12px;
		line-height: 24px;
	}
	
	.list {
		font-size: 12px;
		padding: 0 8px;
		color: #999999;
	}
	
	.item {
		height: 40px;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	
	.label {
		color: #FFFFFF;
	}
	
	.value {
		display: flex;
		align-items: center;
	}
	
	
</style>
