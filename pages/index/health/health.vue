<template>
	<view class="page">
		<view class="tabBar">
			<template v-for="(item,index) in TabList">
				<text :key='index' :class="activeIndex == index ? 'tab-active' : ''" @click="changeTab(index)">
					{{item}}
				</text>
			</template>
		</view>
		<view class="content" v-show='activeIndex==0'>
			<template v-for="(item,index) in GuideList">
				<view class='guide' :key='index' @click='enterDetail'>
					<image :src="item.img" mode=""></image>
					<view class="message">
						<text class='title'>{{item.title}}</text>
						<text class='text'>{{item.text}}</text> 
						<view class="info">
							<view class='date'> 
								<image src="../../../static/icon_time.png" mode="widthFix"></image>
								<text>{{item.date}}</text>
							</view>
							<view class='visit'>
								<image src="../../../static/icon_browse.png" mode="widthFix"></image>
								<text>{{item.visiter}}</text>
							</view>
						</view>
					</view>
				</view>
			</template>
		</view>
		<view class="content" v-show='activeIndex==1'>
			<template v-for="(item,index) in videoList">
				<view class='video' :key='index' @click='enterVideo'>
					<view class="picture">
						<image :src="item.img" mode=""></image>
						<image src="../../../static/play.png" mode="" class="play-icon"></image>
					</view>
					<view class="message">
						<text class='title'>{{item.title}}</text>
						<view class="info">
							<view class='date'> 
								<image src="../../../static/icon_time.png" mode="widthFix"></image>
								<text>{{item.date}}</text>
							</view>
							<view class='visit'>
								<image src="../../../static/icon_browse.png" mode="widthFix"></image>
								<text>{{item.visiter}}</text>
							</view>
						</view>
					</view>
				</view>
			</template>
		</view>
		<view class="content" v-show='activeIndex==2'>
			<template v-for="(item,index) in GuideList">
				<view class='guide' :key='index' @click='enterDetail'>
					<image :src="item.img" mode=""></image>
					<view class="message">
						<text class='title'>{{item.title}}</text>
						<text class='text'>{{item.text}}</text>
						<view class="info">
							<view class='date'> 
								<image src="../../../static/icon_time.png" mode="widthFix"></image>
								<text>{{item.date}}</text>
							</view>
							<view class='visit'>
								<image src="../../../static/icon_browse.png" mode="widthFix"></image>
								<text>{{item.visiter}}</text>
							</view>
						</view>
					</view>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				TabList: [
					'最新指南',
					'教育视频',
					'相关文章'
				],
				activeIndex: 0,
				GuideList: [{
					img: 'http://img5.imgtn.bdimg.com/it/u=1658374073,3364944004&fm=26&gp=0.jpg',
					title: '体重管理必备条件-忌节食',
					text: '体重管理是一门学问，节食方法往往会影响身体健康状态，导致哈哈哈哈哈',
					date: '2019.10.30  20:43',
					visiter: '185'
				},
				{
					img: 'http://img5.imgtn.bdimg.com/it/u=1658374073,3364944004&fm=26&gp=0.jpg',
					title: '体重管理必备条件-忌节食',
					text: '体重管理是一门学问，节食方法往往会影响身体健康状态，导致哈哈哈哈哈',
					date: '2019.10.30  20:43',
					visiter: '185'
				},
				{
					img: 'http://img5.imgtn.bdimg.com/it/u=1658374073,3364944004&fm=26&gp=0.jpg',
					title: '体重管理必备条件-忌节食',
					text: '体重管理是一门学问，节食方法往往会影响身体健康状态，导致哈哈哈哈哈',
					date: '2019.10.30  20:43',
					visiter: '185'
				}],
				videoList:[{
					img: 'http://img0.imgtn.bdimg.com/it/u=1901739916,3856785126&fm=26&gp=0.jpg',
					title: '防止便秘-多吃蔬菜就可以解决便秘？',
					date: '2019.10.30  20:43',
					visiter: '1855'
				},
				{
					img: 'http://img0.imgtn.bdimg.com/it/u=1901739916,3856785126&fm=26&gp=0.jpg',
					title: '防止便秘-多吃蔬菜就可以解决便秘？',
					date: '2019.10.30  20:43',
					visiter: '1855'
				}]
			}
		},
		methods: {
			changeTab(e) {
				this.activeIndex = e;
			},
			enterDetail(){
				uni.navigateTo({
					url:'article'
				})
			},
			enterVideo(){
				uni.navigateTo({
					url: 'video'
				})
			}
		}
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
	}

	.tabBar {
		display: flex;
		justify-content: space-around;
		height: 90rpx;
		line-height: 90rpx;
		font-size: 28rpx;
		color: #80899c;
		background-color: #fff;
		font-family: PingFang-SC-Bold;

		.tab-active {
			font-size: 34rpx;
			color: #333;
			position: relative;

			&::after {
				content: "";
				position: absolute;
				width: 80rpx;
				height: 1rpx;
				left: 50%;
				transform: translate(-50%,0);
				bottom: 15rpx;
				border-bottom: 6rpx solid #a69eff;
				border-radius: 5rpx;
			}
		}
	}

	.content {
		padding: 10rpx 20rpx 120rpx 20rpx;

		.guide {
			display: flex;
			padding: 30rpx;
			margin-bottom: 10rpx;
			background-color: #fff;

			image {
				flex: 0 0 230rpx;
				height: 172rpx;
			}

			.message {
				display: flex;
				flex-direction: column;
				justify-content: space-between;
				padding-left: 20rpx;
				.title {
					display: block;
					color: #80899c;
					font-size: 30rpx;
					font-weight: bold;
				}

				.text {
					width: 400rpx;
					font-size: 26rpx;
					color: #999999;
					letter-spacing: 1px;
					overflow: hidden;
					text-overflow: ellipsis;
					display: -webkit-box;
					-webkit-line-clamp: 2;
					-webkit-box-orient: vertical;
				}
				
				.info{
					display: flex;
					justify-content: space-between;
					font-size: 24rpx;
					color: #cccccc;
					.date{
						display: flex;
						align-items: center;
						image{
							flex: 0 0 26rpx;
							width: 26rpx;
							heihgt: 26rpx;
							padding-right: 12rpx;
						}
					}
					.visit{
						display: flex;
						align-items: center;
						image{
							flex: 1 1 30rpx;
							width: 30rpx;
							height: 25rpx;
							padding-right: 12rpx;
						}
					}
				}
			}
		}
		.video{
			margin-top: 10rpx;
			background-color: #fff;
			.picture{
				position: relative;
				image{
					width: 100%;
					height: 355rpx;
				}
				.play-icon{
					position: absolute;
					top:50%;
					left: 50%;
					transform: translate(-50%,-50%);
					width: 80rpx;
					height: 80rpx;
				}
			}
			.message{
				padding: 0 30rpx;
				.title{
					font-size: 30rpx;
					color: #80899c;
				}
				.info{
					display: flex;
					justify-content: space-between;
					width: 380rpx;
					padding: 20rpx 0;
					margin-bottom: 30rpx;
					font-size: 24rpx;
					color: #cccccc;
					.date{
						display: flex;
						align-items: center;
						image{
							flex: 0 0 26rpx;
							width: 26rpx;
							heihgt: 26rpx;
							padding-right: 12rpx;
						}
					}
					.visit{
						display: flex;
						align-items: center;
						image{
							flex: 1 1 30rpx;
							width: 30rpx;
							height: 25rpx;
							padding-right: 12rpx;
						}
					}
				}
			}
		}
}
</style>
