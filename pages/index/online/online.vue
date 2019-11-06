<template>
	<view class="page">
		<view class="content">
			<template v-for="(item,index) in questionnaireList">
				<view class='guide' :key='index' @click='enterDetail'>
					<image :src="item.img" mode=""></image>
					<view class="message">
						<text class='title'>{{item.title}}</text>
						<view class="info">
							<view class='date'>
								<image src="../../../static/icon_time.png" mode="widthFix"></image>
								<text>{{item.date}}</text>
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
				questionnaireList: [{
					img: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1487361593,1220453903&fm=26&gp=0.jpg',
					title: '健康调查简表，SF-36',
					date: '2019.10.30 - 2019.11.25'
				},
				{
					img: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1487361593,1220453903&fm=26&gp=0.jpg',
					title: '健康调查简表，SF-36',
					date: '2019.10.30 - 2019.11.25'
				},{
					img: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1487361593,1220453903&fm=26&gp=0.jpg',
					title: '健康调查简表，SF-36',
					date: '2019.10.30 - 2019.11.25'
				}]
			}
		},
		methods: {
			enterDetail() {

			}
		}
	}
</script>

<style lang="less">
	
	page{
		height: 100%;
		background-color: #f9fafd;
	}
	.content {
		padding: 20rpx 20rpx 120rpx 20rpx;

		.guide {
			display: flex;
			padding: 30rpx;
			margin-bottom: 20rpx;
			background-color: #fff;

			image {
				flex: 0 0 160rpx;
				height: 120rpx;
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

				.info {
					display: flex;
					justify-content: space-between;
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
				}
			}
		}
	}
</style>
