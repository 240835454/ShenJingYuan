<template>
	<view class="page">
		<video src="http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400"
		 controls></video>
		<view class="content">
			<text class='title'>{{title}}</text>
			<view class="info">
				<view class='date'>
					<image src="../../static/icon_time.png" mode="widthFix"></image>
					<text>{{date}}</text>
				</view>
				<view class='visit'>
					<image src="../../static/icon_browse.png" mode="widthFix"></image>
					<text>{{visiter}}</text>
				</view>
			</view>
			<view class="">
				<text>
					避免高GI的食物GI =（Glycemic Index。
				</text>
			</view>
		</view>
		<view class="recommend">
			<text class='topic'>推荐视频</text>
		</view>
		<view class="footer">
			<template v-for="(item,index) in videoList">
				<view class='video' :key='index' @click='enterVideo'>
					<view class="picture">
						<image :src="item.img" mode=""></image>
						<image src="../../static/play.png" mode="" class="play-icon"></image>
					</view>
					<view class="message">
						<text class='title'>{{item.title}}</text>
						<view class="info">
							<view class='date'> 
								<image src="../../static/icon_time.png" mode="widthFix"></image>
								<text>{{item.date}}</text>
							</view>
							<view class='visit'>
								<image src="../../static/icon_browse.png" mode="widthFix"></image>
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
				title: "如何在两个月内瘦40斤？",
				date: "2019.10.30  20:43",
				visiter: "1855",
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
				}],
			}
		}
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
	}

	.page {
		video {
			display: block;
			width: 100%;
			height: 380rpx;
		}
	}

	.content {
		padding: 40rpx 60rpx;
		background-color: #fff;
		.title {
			font-size: 38rpx;
			color: #333333;
		}

		.info {
			display: flex;
			justify-content: space-between;
			width: 405rpx;
			font-size: 24rpx;
			color: #cccccc;
			padding-top: 24rpx;

			.date {
				display: flex;
				align-items: center;

				image {
					flex: 0 0 26rpx;
					width: 26rpx;
					heihgt: 26rpx;
					padding-right: 12rpx;
				}
			}

			.visit {
				display: flex;
				align-items: center;

				image {
					flex: 1 1 30rpx;
					width: 30rpx;
					height: 25rpx;
					padding-right: 12rpx;
				}
			}
		}
	}

	.recommend {
		margin: 30rpx 0;
		.topic {
			display: block;
			padding-left: 20rpx;
			font-size: 34rpx;
			color: #333;
			position: relative;
			&::after {
				content: "";
				position: absolute;
				bottom: -5rpx;
				left: 20rpx;
				width: 80rpx;
				height: 6rpx;
				background-color: #a69eff;
				border-radius: 3px;
			}
		}
	}
	
	.footer {
		padding: 10rpx 20rpx 120rpx 20rpx;
		.video {
			margin-top: 10rpx;
			background-color: #fff;
	
			.picture {
				position: relative;
	
				image {
					width: 100%;
					height: 355rpx;
				}
	
				.play-icon {
					position: absolute;
					top: 50%;
					left: 50%;
					transform: translate(-50%, -50%);
					width: 80rpx;
					height: 80rpx;
				}
			}
	
			.message {
				padding: 0 30rpx;
	
				.title {
					font-size: 30rpx;
					color: #80899c;
				}
	
				.info {
					display: flex;
					justify-content: space-between;
					width: 380rpx;
					padding: 20rpx 0;
					margin-bottom: 30rpx;
					font-size: 24rpx;
					color: #cccccc;
	
					.date {
						display: flex;
						align-items: center;
	
						image {
							flex: 0 0 26rpx;
							width: 26rpx;
							heihgt: 26rpx;
							padding-right: 12rpx;
						}
					}
	
					.visit {
						display: flex;
						align-items: center;
	
						image {
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
