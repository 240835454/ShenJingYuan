<template>
	<view class="page">
		<view class="content">
			<view class="box">
				<view class="title">
					<text>风险值</text>
					<text class='standard'>评估风险标准值</text>
					<text class='test'>测试评估风险值</text>
				</view>
				<view class="qiun-charts">
					<canvas canvas-id="canvasArea" id="canvasArea" class="charts" @touchstart="touchArea"></canvas>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uCharts from '../../../public/js/u-charts.js';
	var _self;
	var canvaArea = null;

	export default {
		data() {
			return {
				cWidth: '',
				cHeight: '',
				pixelRatio: 1,
			}
		},
		onLoad() {
			_self = this;
			this.cWidth = uni.upx2px(750);
			this.cHeight = uni.upx2px(500);
			this.getServerData();
		},
		methods: {
			getServerData() {
				uni.request({
					url: 'https://www.ucharts.cn/data.json',
					data: {},
					success: function(res) {
						console.log(res.data.data)
						let Area = {
							categories: [],
							series: []
						};
						//这里我后台返回的是数组，所以用等于，如果您后台返回的是单条数据，需要push进去
						Area.categories = res.data.data.Area.categories;
						Area.series = res.data.data.Area.series;
						_self.showArea("canvasArea", Area);
					},
					fail: () => {
						_self.tips = "网络错误，小程序端请检查合法域名";
					},
				});
			},
			showArea(canvasId, chartData) {
				canvaArea = new uCharts({
					$this: _self,
					canvasId: canvasId,
					type: 'area',
					fontSize: 11,
					legend: true,
					dataLabel: false,
					dataPointShape: true,
					background: '#FFFFFF',
					pixelRatio: _self.pixelRatio,
					categories: chartData.categories,
					series: chartData.series,
					animation: true,
					xAxis: {
						type: 'grid',
						gridColor: '#CCCCCC',
						gridType: 'dash',
						dashLength: 8
					},
					yAxis: {
						gridType: 'dash',
						gridColor: '#CCCCCC',
						dashLength: 8,
						splitNumber: 5,
						min: 10,
						max: 180,
					},
					width: _self.cWidth * _self.pixelRatio,
					height: _self.cHeight * _self.pixelRatio,
					extra: {
						area: {
							type: 'straight',
							opacity: 0.2,
							addLine: true,
							width: 2
						}
					}
				});
			},
			touchArea(e) {
				canvaArea.showToolTip(e, {
					format: function(item, category) {
						return category + ' ' + item.name + ':' + item.data
					}
				});
			}
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

	.qiun-charts {
		width: 650rpx;
		height: 500rpx;
		background-color: #FFFFFF;
	}

	.charts {
		width: 650rpx;
		height: 500rpx;
		background-color: #FFFFFF;
	}
</style>
