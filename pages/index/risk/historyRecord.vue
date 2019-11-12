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
			<view class="risk-info">
				<text class='record'>风险评估记录</text>
				<template v-for='(item,index) in reportList'>
					<view class='info-item' :key='index' @click="enterReport">
						<text class='name'>
							{{item.name}}
						</text>
						<text class='value' :class="item.value == '高风险' ? 'height' : ''">
							{{item.value}}
						</text>
					</view>
				</template>
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
				series: [{
						color: "#a69eff",
						data: [100, 80, 95, 150, 112, 132],
						index: 0
					},
					{
						color: "#a6b5d5",
						data: [70, 40, 65, 100, 44, 68],
						index: 0
					}
				],
				reportList: [{
						name: '评估报告2019.10.30',
						value: '低风险'
					},
					{
						name: '评估报告2019.10.30',
						value: '高风险'
					}
				]
			}
		},
		onLoad() {
			_self = this;
			this.cWidth = uni.upx2px(750);
			this.cHeight = uni.upx2px(500);
			this.getServerData();
		},
		methods: {
			enterReport(){
				uni.navigateTo({
					url: 'report'
				})
			},
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
						// Area.series = res.data.data.Area.series;
						Area.series = _self.series;
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
					legend: {
						show: false
					},
					dataLabel: false,
					dataPointShape: true,
					dataPointShapeType: 'hollow',
					background: '#FFFFFF',
					pixelRatio: _self.pixelRatio,
					categories: chartData.categories,
					series: chartData.series,
					animation: true,
					xAxis: {
						type: 'grid',
						gridColor: '#cccccc',
						gridType: 'solid',
						dashLength: 8,
						splitNumber: 5,
					},
					yAxis: {
						data: [{
							min: 10,
							max: 180,
						}],
						gridType: 'solid',
						gridColor: '#cccccc',
						dashLength: 8,
						splitNumber: 5,
					},
					width: _self.cWidth * _self.pixelRatio,
					height: _self.cHeight * _self.pixelRatio,
					extra: {
						area: {
							type: 'curve',
							opacity: 0.4,
							addLine: true,
							width: 2,
							gradient: true
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
	.content {
		padding: 20rpx;
		font-family: PingFang-SC-Medium;

		.box {
			padding: 40rpx 20rpx 20rpx 20rpx;
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

		.risk-info {
			text-align: left;
			background-color: #fff;
			padding-bottom: 120rpx;
			position: relative;
			&::after{
				content: "";
				display: inline-block;
				position: absolute;
				bottom: 120rpx;
				width: 100%;
				height:1rpx;
				border-bottom: 1rpx solid #e5e5e5;
			}
			.record {
				display: block;
				padding: 30rpx 0 40rpx 30rpx;
				font-size: 34rpx;
				color: #333333;
				position: relative;
				&::after{
					content: "";
					position: absolute;
					left: 30rpx;
					bottom: 30rpx;
					width: 80rpx;
					height: 6rpx;
					border-bottom: 6rpx solid #a69eff;
					border-radius: 3rpx;
				}
			}
		}
	}
</style>
