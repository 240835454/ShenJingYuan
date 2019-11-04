<template>
	<view class="page">
		<view class="tabBar">
			<template v-for="(item,index) in TabList">
				<text :key='index' :class="activeIndex == index ? 'tab-active' : ''" @click="changeTab(index)">
					{{item}}
				</text>
			</template>
		</view>
		<view class="content">
			<view class="box">
				<view class="picture">
					<image src="../../../static/fengxian.png" mode="widthFix">
					</image>
					<text class='test-result'>
						{{rate}}
					</text>
					<text class='result'>测试结果为：{{result}}</text>
					<text class='result'>最佳风险值：{{best}}</text>
					<text class='report' @click='enterReport'>
						查看评估风险报告
					</text>
				</view>
			</view>
			<template v-for='(item,index) in infoList'>
				<view class="info-item" :key='index'>
					<text class='name'>
						{{item.name}}
					</text>
					<text class='value'>
						{{item.value}}
					</text>
				</view>
			</template>
			<view class="info-item" @click="historyRecord">
				<text class="name">
					查看历史评估记录
				</text>
				<text class='value'>
					&nbsp;
				</text>
			</view>
			<view class="footer">
				<text class='button' @click='beginEvaluate'>
					开始评估
				</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				TabList: [
					'上尿路损害发生率',
					'神经源性膀胱泌尿系感染'
				],
				infoList: [{
						name: '性别',
						value: '男性'
					},
					{
						name: '感染病史',
						value: '有'
					},
					{
						name: '膀胱顺应性',
						value: '正常或高'
					},
					{
						name: '疾病病程',
						value: '<=5年'
					}, {
						name: '大便失禁',
						value: '无'
					}
				],
				activeIndex: 0,
				result: '低风险',
				best: '0 . 6%',
				rate: '1.5'
			}
		},
		methods: {
			changeTab(e) {
				this.activeIndex = e;
			},
			beginEvaluate(){ 
				uni.navigateTo({
					url: 'evaluate'
				})
			},
			enterReport(){
				uni.navigateTo({
					url: 'report'
				})
			},
			historyRecord(){
				uni.navigateTo({
					url: 'historyRecord'
				})
			}
		}
	}
</script>

<style lang='less'>
	.page {
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
				left: 38%;
				bottom: 15rpx;
				border-bottom: 6rpx solid #a69eff;
				border-radius: 3px;
			}
		}
	}

	.content {
		padding: 10rpx 20rpx 40rpx;
		color: #80899c;

		.box {
			background-color: #fff;
			font-family: PingFang-SC-Medium;

			.picture {
				padding: 40rpx 80rpx 20rpx;
				text-align: center;
				position: relative;

				image {
					width: 550rpx;
					height: 230rpx;
				}

				.test-result {
					display: inline-block;
					position: absolute;
					top: 110rpx;
					left: 40%;
					font-size: 72rpx;
					font-family: '064-CAI978';
					color: #fffefe;

					&::after {
						content: "%";
						padding-left: 20rpx;
						font-size: 40rpx;
					}
				}

				.result {
					display: block;
					padding-top: 20rpx;
					font-size: 34rpx;
				}

				.report {
					display: inline-block;
					padding: 20rpx 64rpx;
					margin: 20rpx 0;
					color: #a69eff;
					border: 1rpx solid rgba(166, 158, 255, 0.3);
					font-size: 34rpx;
				}
			}
		}

		.info-item {
			display: flex;
			justify-content: space-between;
			align-items: center;
			position: relative;
			padding: 40rpx 80rpx;
			font-size: 30rpx;
			border-top: 1rpx solid #e6e7eb;
			background-color: #fff;

			.name {
				&::before {
					content: "";
					position: absolute;
					top: 44%;
					left: 50rpx;
					display: inline-block;
					width: 4rpx;
					height: 20rpx;
					border-left: 4rpx solid #b2b9c9;
				}
			}

			.value {
				font-size: 28rpx;
				color: #b2b2b2;
				position: relative;

				&::after {
					content: "";
					display: inline-block;
					width: 18rpx;
					height: 18rpx;
					top: 28%;
					right: -40rpx;
					border-top: 1rpx solid #e5e5e5;
					border-right: 1rpx solid #e5e5e5;
					transform: rotate(45deg);
					position: absolute;

				}
			}
		}

		.footer {
			padding: 40rpx 0 20rpx 0;
			text-align: center;
			background-color: #fff;
			border-top: 1rpx solid #e6e7eb;
			.button {
				display: inline-block;
				padding: 20rpx 200rpx;
				font-size: 34rpx;
				background-image: linear-gradient(0deg,
					#a69eff 0%,
					#ccc7ff 100%),
					linear-gradient(#ffffff,
					#ffffff);
				background-blend-mode: normal,
					normal;
				color: #fff;
			}
		}
	}
</style>
