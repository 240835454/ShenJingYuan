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
					<canvas canvas-id="canvasColumn" id="canvasColumn" class="charts"></canvas>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uCharts from '../../../public/js/u-charts.js';
	export default {
		data() {
			return {
				cWidth: '',
				cHeight: '',
				pixelRatio: 1,
				serverData: ''
			}
		},
	methods: {},
		components: {}
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
