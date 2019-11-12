<template>
	<view class="page">
		<view class="content">
			<view class="box">
				<text class='evaluateValue'>评估风险值：{{riskValue}}</text>
				<text class='bestValue'>最佳风险值：0.8 %</text>
				<image src="../../../static/插图.png" mode="aspectFit"></image>
				<view class="result">
					<text class='result-item'>
						评估风险值{{riskValue}} < 3% </text> <text class='result-item'>
							评估结果为：{{result}}
					</text>
				</view>
				<view class="notice">
					<text class='title'>
						预防缓解尿失禁三大运动
					</text>
					<view class="text">
						<text class='topic'>1.锁紧阴道运动</text>
						<text>
							首先准备好瑜伽垫，然后平躺在上面，或者平躺在床上也可以。一边吸气一边尽量利用肛门的力量用力紧缩阴道，呼气的时候再慢慢放下来。以完成呼吸过程为一组，每次做8组就侧躺休息一下。要注意的是，在做动作时不要屏住呼气，要结合好呼吸的规律，集中注意，慢慢运动。
						</text>
					</view>
					<view class="text">
						<text class='topic'>2.分腿运动</text>
						<text>
							同样，首先平躺在瑜伽垫上或床上并，利用嘴呼吸，在呼气的同时按住膝盖尽量抬起上半身；而后用回鼻子吸气，同时把膝盖放下，恢复平躺的姿势。这两个动作为一组，每次重复做五次后就侧躺休息。
						</text>
					</view>
					<view class="text">
						<text class="topic">3.骨盘底肌肉锻炼</text>
						<text>
							先平躺下来，用枕头或者较厚的毛巾垫在后脑，双手分别放在身体两侧，弓起膝盖，平放脚掌；然后用力收紧骨盘底肌肉，坚持一段时间后再放松。以收紧放松为一组，每次要做十组，每日至少要做三到五次。所以当孕晚期尿失禁现象发生时，孕妈妈们不必过分担心或者羞愧，因为这是很正常的现象。另外，孕妈妈们在做这下动作时，最后有人在旁协助，因为孕妇在孕晚期身体没有那么灵活，稍显笨重，所以如果有丈夫在旁协助，即健康，又可以增进夫妻间的感情。
						</text>
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
				riskValue: '1.5 %',
				result: "低风险"
			}
		}
	}
</script>

<style lang="less">
	.content {
		padding: 20rpx;
		font-family: PingFang-SC-Medium;

		.box {
			position: relative;
			padding: 40rpx 20rpx;
			background-color: #fff;
			text-align: center;

			image {
				width: 550rpx;
				height: 365rpx;
			}

			.evaluateValue {
				position: absolute;
				top: 140rpx;
				left: 50%;
				transform: translate(-50%, 0);
				display: block;
				font-size: 30rpx;
				color: #80899c;
			}

			.bestValue {
				.evaluateValue;
				top: 240rpx;
				color: #a69eff;
			}

			.result {
				padding: 40rpx 0;
				font-size: 34rpx;
				color: #80899c;

				.result-item {
					display: block;
				}
			}

			.notice {
				text-align: left;

				.title {
					display: block;
					padding: 60rpx 0;
					font-size: 38rpx;
					text-align: center;
					color: #333;
				}

				.text {
					.topic {
						display: block;
						padding: 30rpx 0 5rpx 0;
						text-align: left;
						font-size: 34rpx;
						color: #80899c;
					}

					text {
						font-size: 28rpx;
						color: #666666;
						letter-spacing: 1rpx;
					}
				}
			}
		}
	}
</style>
