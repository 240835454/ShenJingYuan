<template>
	<view class="content">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" indicator-color="rgba(255,255,255,0.3)"
		 indicator-active-color="rgba(255,255,255,1)" :duration="1000" circular="true" class="swiper">
			<template v-for='(item,index) in imgList'>
				<swiper-item :key='index' class='swiper-item'>
					<image :src="item" mode="" class='img'></image>
				</swiper-item>
			</template>
		</swiper>
		<view class="tabBar">
			<view class="flex">
				<view class="item" @click='enterRisk'>
					<image src="../../static/图层18.png" mode="aspectFill"></image>
					<view class="text-box">
						<text>风险评估</text>
						<text class='en-text'>The risk assessment</text>
					</view>
				</view>
				<view class="item">
					<image src="../../static/图层20.png" mode="aspectFill"></image>
					<view class="text-box">
						<text>健康知识</text>
						<text class='en-text'>Health knowledge</text>
					</view>
				</view>
			</view>
			<view class="flex">
				<view class="item">
					<image src="../../static/图层19.png" mode="aspectFill"></image>
					<view class="text-box">
						<text>膀胱管理</text>
						<text class='en-text'>Bladder management</text>
					</view>
				</view>
				<view class="item">
					<image src="../../static/图层22.png" mode="aspectFill"></image>
					<view class="text-box">
						<text>在线评测</text>
						<text class='en-text'>The online evaluation</text>
					</view> 
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello', 
				imgList: [
					'http://img2.imgtn.bdimg.com/it/u=3659188243,1562659949&fm=26&gp=0.jpg',
					'http://img2.imgtn.bdimg.com/it/u=3659188243,1562659949&fm=26&gp=0.jpg',
					'http://img2.imgtn.bdimg.com/it/u=3659188243,1562659949&fm=26&gp=0.jpg',
				],
			}
		},
		onLoad() {},
		methods: {
			enterRisk(){
				uni.navigateTo({
					url:'risk/risk'
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100vh;
		padding: 10px;
		background-color: #f9fafd;
		box-shadow: inset 0px -2px 5px 0px rgba(168, 168, 168, 0.46);
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}

	.swiper {
		width: 100%;
		height: 355rpx;
	}

	.swiper-item {
		width: 100%;
	}

	.img {
		width: 100%;
	}

	.tabBar {
		display: flex;
		flex-direction: column;
		width: 100%;
	}

	.tabBar .flex {
		display: flex;
		justify-content: space-between;
		padding: 20px 0 0 0;
	}

	.tabBar .flex .item {
		width: 340rpx;
		background-color: #fff;
	}

	.text-box {
		padding: 30rpx;
		font-family: PingFang-SC-Medium;
		color: #80899c;
	}

	.tabBar .flex image {
		width: 100%;
		height: 255rpx;
	}

	.tabBar .flex text {
		display: block;
		font-size: 34rpx;
	}

	.tabBar .flex .en-text {
		position: relative;
		font-size: 20rpx;
	}

	.en-text::after {
		content: "";
		position: absolute;
		right: 0;
		bottom: 0;
		width: 30rpx;
		height: 2rpx;
		border-bottom: 3rpx solid #a6b5d5;
		opacity: 0.5;
	}
</style>
