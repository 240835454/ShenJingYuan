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
		<view class="tabBar-box">
			<view class="flex">
				<view class="item" @click='enterRisk'>
					<image src="../../static/图层18.png" mode="aspectFill"></image>
					<view class="text-box">
						<text>风险评估</text>
						<text class='en-text'>The risk assessment</text>
					</view>
				</view>
				<view class="item" @click='enterHealth'>
					<image src="../../static/图层20.png" mode="aspectFill"></image>
					<view class="text-box">
						<text>健康知识</text>
						<text class='en-text'>Health knowledge</text>
					</view>
				</view>
			</view>
			<view class="flex">
				<view class="item" @click='enterBladder'>
					<image src="../../static/图层19.png" mode="widthFix"></image>
					<view class="text-box">
						<text>膀胱管理</text>
						<text class='en-text'>Bladder management</text>
					</view>
				</view>
				<view class="item" @click='enterOnline'>
					<image src="../../static/图层22.png" mode="aspectFill"></image>
					<view class="text-box">
						<text>在线评测</text>
						<text class='en-text'>The online evaluation</text>
					</view>
				</view>
			</view>
		</view>
		<view class="mask" v-show="isHide">
		</view>
		<view class="declare" v-show="isHide">
			<text class='title'>免责声明</text>
			<text class='text'>鉴于本系统使用非人工检索/分析方式，无法确定您输入的条件进行是否合法，所以本系统对检索/分析出的结果不承担责任。如果因以本系统的检索/分析结果作为任何商业行为或者学术研究的依据而产生不良后果，本系统不承担任何法律责任。</text>
			<view class="button-box">
				<text class='cancel' @click='close'>取消</text>
				<text class='submit' @click='submit'>确定</text>
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
				isHide: true
			}
		},
		onLoad() {
			uni.hideTabBar({
				
			})
		},
		methods: {
			enterRisk() {
				uni.navigateTo({
					url: 'risk/risk'
				})
			},
			enterHealth() {
				uni.navigateTo({
					url: 'health/health'
				})
			},
			enterBladder() {
				uni.navigateTo({
					url: 'bladder/bladder'
				})
			},
			enterOnline() {
				uni.navigateTo({
					url: 'online/online'
				})
			},
			close(){
				this.isHide = false; 
				uni.showTabBar({
					
				})
			},
			submit(){
				uni.navigateTo({
					url: 'info/info'
				})
			}
		}
	}
</script>

<style lang="less">
	.content {
		display: flex;
		flex-direction: column;
		align-items: center; 
		justify-content: center;
		padding: 10px 20rpx 0rpx;
		background-color: #f9fafd;
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

	.tabBar-box {
		display: flex;
		flex-direction: column;
		width: 100%;
	}

	.tabBar-box .flex {
		display: flex;
		justify-content: space-between;
		padding: 20px 0 0 0;
	}

	.tabBar-box .flex .item {
		width: 340rpx;
		background-color: #fff;
	}

	.text-box {
		padding: 30rpx;
		font-family: PingFang-SC-Medium;
		color: #80899c;
	}

	.tabBar-box .flex image {
		width: 100%;
		height: 255rpx;
	}

	.tabBar-box .flex text {
		display: block;
		font-size: 34rpx;
	}

	.tabBar-box .flex .en-text {
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

	.declare {
		position: absolute;
		top: 200rpx;
		left: 50%;
		transform: translateX(-50%);
		width: 600rpx;
		height: 540rpx;
		background-color: #fff;
		font-size: 34rpx;
		z-index: 10;
		color: #333333;
		letter-spacing: 1px;
		.title {
			display: block;
			padding: 48rpx 0 40rpx;
			text-align: center;
		}
		.text{
			display: block;
			padding: 0 40rpx;
			line-height: 40rpx;
			font-size: 28rpx;
			letter-spacing: 1rpx;
			color: #80899c;
		}

		.button-box {
			display: flex;
			justify-content: space-between;
			padding: 80rpx 40rpx; 
			background-color: #fff;

			.submit { 
				padding: 16rpx 90rpx;
				color: #fff;
				background-image: linear-gradient(0deg,
					#a69eff 0%,
					#ccc7ff 100%),
					linear-gradient(#ffffff,
					#ffffff);
				background-blend-mode: normal,
					normal;
			}

			.cancel {
				padding: 15.5rpx 89.5rpx;
				color: #80899c;
				background-color: #fff;
				border: solid 1px #80899c; 
			}
		}
	}
</style>
