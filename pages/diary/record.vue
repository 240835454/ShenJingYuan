<template>
	<view class="page">
		<view class="box">
			<view class="content">
				<view class="title">
					<text>基本信息</text>
				</view>
			</view>
			<view>
				<view class="item">
					<text class='name water'>饮水量</text>
					<input type="text" :value="waterValue" class='input-box' placeholder-class="phcolor" disabled placeholder="请选择饮水量"
					 maxlength="5" @click="openOne" />
					<text class='name'>排尿量</text>
					<input type="text" :value="urinateValue" class='input-box' placeholder-class="phcolor" disabled placeholder="请选择排尿量"
					 maxlength="5" @click="openTwo" />
					<text class='name surplus'>残留量</text>
					<input type="text" :value="surplusValue" class='input-box' placeholder-class="phcolor" disabled placeholder="请选择残留量"
					 maxlength="5" @click="openThree" />
					<view class="footer">
						<text class='button' @click='confirm'>
							确定
						</text>
					</view>
				</view>
			</view>
		</view>
		<w-picker v-if="selectList.length!=0" mode="selector" :defaultVal="['女']" @confirm="onConfirmWater" ref="selectorOne"
		 :selectList="selectList" :themeColor='themeColor' :leftTopText='water'></w-picker>
		<w-picker v-if="selectList.length!=0" mode="selector" :defaultVal="['女']" @confirm="onConfirmUrinate" ref="selectorTwo"
		 :selectList="selectList" :themeColor='themeColor' :leftTopText='urinate'></w-picker>
		<w-picker v-if="selectList.length!=0" mode="selector" :defaultVal="['女']" @confirm="onConfirmSurplus" ref="selectorThree"
		 :selectList="selectList" :themeColor='themeColor' :leftTopText='surplus'></w-picker>
	</view>
</template>

<script>
	import wPicker from "@/components/w-picker/w-picker.vue";
	export default {
		data() {
			return {
				array: ['1杯', '2杯', '3杯', '4杯'],
				index: 0,
				selectList: [{
					label: '1杯',
					value: '1'
				}, {
					label: '2杯',
					value: '2'
				}, {
					label: '3杯',
					value: '3'
				}, {
					label: '4杯',
					value: '4'
				}],
				themeColor: '#a69eff',
				water: '饮水量',
				urinate: '排尿量',
				surplus: '残留量',
				waterValue: '',
				urinateValue: '',
				surplusValue: ''
			}
		},
		methods: {
			openOne() {
				this.$refs.selectorOne.show();
			},
			openTwo() {
				this.$refs.selectorTwo.show();
			},
			openThree() {
				this.$refs.selectorThree.show();
			},
			onConfirmWater(e) {
				this.waterValue = e.result;
			},
			onConfirmUrinate(e) {
				this.urinateValue = e.result;
			},
			onConfirmSurplus(e) {
				this.surplusValue = e.result;
			},
			confirm() {
				uni.navigateBack({
					delta: 1
				});
			}
		},
		components: {
			wPicker
		}
	}
</script>

<style lang="less">
	.box {
		padding: 20rpx;

		.content {
			background-color: #fff;
			padding: 30rpx;

			.title {
				position: relative;
				display: block;
				font-size: 34rpx;
				color: #333333;

				&::before {
					content: "";
					position: absolute;
					left: 0;
					bottom: -10rpx;
					width: 80rpx;
					height: 6rpx;
					background-color: #a69eff;
					border-radius: 3rpx;
				}
			}
		}

		.item {
			color: #80899c;
			background-color: #fff;
			padding: 0 20rpx;

			.name {
				display: block;
				padding-left: 30rpx;
				font-size: 34rpx;
				position: relative;

				&::before {
					content: "";
					position: absolute;
					top: 25rpx;
					transform: translate(0, -50%);
					left: 10rpx;
					width: 4rpx;
					height: 20rpx;
					border-left: 4rpx solid #b2b9c9;
				}
			}

			picker {
				font-size: 34rpx;
				color: red;
			}

			.water {
				&::after {
					content: " (一杯大约250ml)";
					font-size: 28rpx;
				}
			}

			.surplus {
				&::after {
					content: "（测量后填写，未测量不填写）";
					font-size: 28rpx;
				}
			}

			.input-box {
				position: relative;
				height: 70rpx;
				padding-left: 20rpx;
				margin: 20rpx 0;
				border: 2rpx solid #e0e4ee;
				font-size: 30rpx;

				&::after {
					content: "";
					position: absolute;
					top: 55%;
					transform: translateY(-45%);
					right: 20rpx;
					width: 0;
					height: 0;
					border: solid;
					border-color: #e0e5ee transparent transparent transparent;
					border-width: 12rpx;
				}
			}

			.phcolor {
				font-size: 30rpx;
				color: #cccccc;
			}
		}

		.footer {
			padding: 40rpx 0 60rpx 0;
			text-align: center;
			background-color: #fff;

			.button {
				display: inline-block;
				padding: 20rpx 240rpx;
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
