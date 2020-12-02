<template>
	<view class="changeName">
		<view class="head">
			<navigator class="iconfont iconfanhui" open-type="navigateBack" url="../editPersonalInformation/editPersonalInformation"></navigator>
			<text class="title">{{title}}</text>
		</view>
		
		<view v-if="category === 'name'">
			<view class="label">我的昵称</view>
			<view class="input-box">
				<input v-model="name" placeholder="请输入您的姓名" maxlength="20"/>
				<icon class="iconfont iconshanchu" @click="name = ''"></icon>
			</view>
			<view class="length">{{length}}/20</view>
			<button @click="save('name')">保存</button>
		</view>
		
		<view v-else-if="category === 'account'">
			<view class="label">我的账号</view>
			<view class="input-box">
				<input v-model="account" placeholder="请输入您的抖音账号" maxlength="16"/>
				<icon class="iconfont iconshanchu" @click="account = ''"></icon>
			</view>
			<view class="length">最多16个字，只允许包含字母、数字、下划线和点,三十天内只能修改一次。</view>
			<button @click="save('account')">保存</button>
		</view>
		
		
		<view v-else-if="category === 'introduction'">
			<view class="label">我的简介</view>
			<textarea placeholder="请输入简介,让别人更懂你!" v-model="introduction" class="introduction"></textarea>
			<button @click="save('introduction')">保存</button>
		</view>
		
	</view>
</template>

<script>
	export default {
		props: ['category'],
		data() { 
			return {
				title: '',
				name: '',
				account: '',
				introduction: '',
				userInfo: {}
			}
		},
		methods: {
			save(e){
				switch(e){
					case 'name':
						if(this.name){
							this.userInfo.name = this.name;
							this.setUserInfo();
						} 
					break;
					case 'account':
						if(this.account){
							this.userInfo.account = this.account;
							this.setUserInfo();
						}
					break;
					case 'introduction':
						if(this.introduction){
							this.userInfo.introduction = this.introduction;
							this.setUserInfo();
						}
					break;
				}
			},
			setUserInfo(){
				uni.setStorage({
					key: 'userInfo',
					data: this.userInfo,
					complete: () => {
						uni.navigateBack();
					}
				});
			}
		},
		computed: {
			length(){
				return this.name.length;
			}
		},
		onLoad(options) {
			uni.getStorage({
				key: 'userInfo',
				success: (res) => {
					if(res.data){
						this.userInfo = res.data;
						this.name = res.data.name;
						this.account = res.data.account;
						this.introduction = res.data.introduction;
					}
				}
			});
			switch(options.category){
				case 'name':
					this.title = '编辑姓名';
				break;
				case 'account':
					this.title = '编辑账号';
				break;
				case 'introduction':
					this.title = '编辑简介';
				break;
			}
			
		}
	}
</script>

<style>
	.changeName {
		height: 100%;
		background-color: #000000;
		color: #999999;
		font-size: 14px;
		padding: 0 4px;
		
	}
	
	.head {
		padding-top: 28px;
		text-align: center;
		line-height: 20px;
	}
	
	.iconfanhui {
		float: left;
	}
	
	.title {
		color: #FFFFFF;
		font-size: 16px;
	}
	
	.label {
		margin-top: 16px;   
	}
	
	.input-box {
		height: 40px;
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 16px;
	}
	
	.iconshanchu {
		/* copy的输入框的行高 */
		line-height: 1.4rem;
		/* margin-right: 4px; */
	}
	
	button {
		background-color: #333333;
		color: #ffffff;
		width: 88%;
		margin-top: 40px;
	}
	
	.introduction {
		width: 100%;
		background: #333333;
		line-height: 24px;
	}
	
</style>
