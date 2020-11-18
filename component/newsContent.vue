<template>
	<view class="newsContent">
		<view class="box">
			<view class="icon">
				<!-- 此处可以用循环 -->
				<view class="icon-item">
					<image src="../static/img/users.png" class="img"></image>
					<view>粉丝</view>
				</view>
			</view>
			<view class="icon">
				<view class="icon-item">
					<image src="../static/img/heart.png" class="img"></image>
					<view>点赞</view>
				</view>
			</view>
			<view class="icon">
				<view class="icon-item">
					<image src="../static/img/message.png" class="img"></image>
					<view>评论并@</view>
				</view>
			</view>
			<view class="icon">
				<view class="icon-item">
					<image src="../static/img/us.png" class="img"></image>
					<view>粉丝互动</view>
				</view>
			</view>
		</view>
		<view class="newsList">
			<view class="news-item">
				<view class="author">
					<image src="../static/img/haha.jpg" class="author-img"></image>
				</view>
				<view class="content">
					<view class="desc">
						<view class="author-name">恩克</view>
						<view class="date">星期日</view>
					</view>
					<view class="detail">
						血肠 肉肠 肚包肉 烤全羊
					</view>
				</view>
			</view>
		</view>
		<view class="noMore">没有更多内容了</view>
	</view>
</template>

<script>
</script>

<style>
	
	.box {
		display: flex;
		align-items: center;
		justify-content: space-around;
	}
	
	.icon-item {
		font-size: 12px;
		display: flex;
		flex-direction: column;
		align-items: center;
		height: 60px;
	}
	
	.icon-item>view {
		line-height: 24px;
	}
	
	.img {
		width: 32px;
		height: 32px;
		border-radius: 5px;
	}
	
	.newsList{
		padding: 16px 12px;
		color: #FFFFFF;
	}
	
	.author {
		float: left;
		padding: 0 10px;
	}
	
	.author-img {
		width: 42px;
		height: 42px;
		border-radius: 50%;
	}
	
	.author-name {
		font-size: 16px;
	}
	
	.date {
		font-size: 10px;
		color: #AAAAAA;
	}
	
	.desc {
		display: flex;
		justify-content: space-between;
		align-items: flex-start;
	}
	
	.detail {
		font-size: 12px;
		line-height: 24px;
	}
	
	.noMore {
		height: 48px;
		line-height: 48px;
		font-size: 12px;
		text-align: center;
	}
	
</style>
