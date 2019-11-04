<template>
	<view class="page">
		<view class="content">
			<view class="box">
				<view class="title">
					<text>风险值</text>
					<text class='standard'>评估风险标准值</text>
					<text class='test'>测试评估风险值</text>
				</view>
				<view class="canvasView">
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				updateStatus: false,
				line: {
					legend: {
						data: ['邮件营销']
					},
					xAxis: {
						type: 'category',
						data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
					},
					yAxis: {
						type: 'value',
						data: []
					},
					dataZoom: [{
						type: 'slider',
						start: 30,
						end: 100,
						zoomLock: false,
					}],
					grid: {
						left: 40,
						right: 40,
						bottom: 20,
						top: 40,
						containLabel: true
					},
					series: [{
						data: [],
						data: [820, 932, 901, 934, 1290, 1330, 1320],
						type: 'line',
						color: ['#5eb4e2'], //折线条的颜色
					}]
				}
			}
		},
		methods: {
		}, 
		components: {
		}
	}
</script>

<style lang='less'>
	.page {
		background-color: #f9fafd;
	}

	.content {
		padding: 20rpx;
		font-family: PingFang-SC-Medium;

		.box {
			padding: 40rpx 20rpx;
			background-color: #fff;
			text-align: center;

			.title {
				display: flex;
				justify-content: space-between;
				font-size: 28rpx;
				color: #80899c;

				.standard {
					display: block;
					position: relative;

					&::after {
						content: "";
						position: absolute;
						top: 50%;
						left: -50rpx;
						transform: translate(0, -50%);
						width: 20rpx;
						height: 20rpx;
						border: 6rpx solid #a69eff;
						border-radius: 50%;
					}
				}

				.test {
					.standard;

					&::after {
						border-color: #a6b5d5;
					}
				}
			}
		}
	}

	.ec-canvas {
		display: flex;
		height: 100%;
		flex: 1;
	}

	.canvasView {
		width: 700upx;
		height: 500upx;
	}
</style>
