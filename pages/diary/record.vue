<template>
	<view class="page">
		<view class="box">

			<view class='content'>
				<view class="item">
					<view class='name water'>饮水量<text class='add-icon' @click='showWaterBox'></text></view>
					<view class="result-box" v-if='hasWaterRecord'>
						<input type="text" :value="currentTime" disabled class='short-input-box' />
						<input type="text" :value="waterValue" disabled class='short-input-box' />
					</view>
					<input type="text" class='input-box' placeholder-class="phcolor" disabled placeholder="请选择饮水量" maxlength="5"
					 @click="openOne" v-if='!waterRecord' />
					<view class='name'>排尿量 <text class='add-icon' @click='showUrinateBox'></text></view>
					<view class="result-box" v-if='hasUrinateRecord'>
						<input type="text" :value="currentTime" disabled class='short-input-box' />
						<input type="text" :value="urinateValue" disabled class='short-input-box' />
					</view>
					<input type="text" value="" class='input-box' placeholder-class="phcolor" disabled placeholder="请选择排尿量" maxlength="5"
					 @click="openTwo" v-if='!urinateRecord' />
					<view class='name surplus'>残留量 <text class='add-icon' @click='showSurplusBox'></text></view>
					<view class="result-box" v-if='hasSurplusRecord'>
						<input type="text" :value="currentTime" disabled class='short-input-box' />
						<input type="text" :value="surplusValue" disabled class='short-input-box' />
					</view>
					<input type="number" class='input-box-number' placeholder-class="phcolor" disabled placeholder="请选择残留量" maxlength="5"
					 @click='openThree' v-if='!surplusRecord' />
					<view class="footer">
						<text class='button' @click='confirm'>
							确定
						</text>
					</view>
				</view>
			</view>
		</view>
		<view v-if='isHide'>
			<view class="mask" @click='closeModel'></view>
			<view class="model-box">
				<view class="">
					输入残留量
				</view>
				<view class="surplus-box">
					<input type="number" maxlength="5" @input='surplusInput' class='surplus-input-box' />
				</view>
				<view class="surplus-button-box">
					<text class='cancel' @click='closeModel'>取消</text>
					<text class='confirm' @click='onConfirmSurplus'>确定</text>
				</view>
			</view>
		</view>
		<w-picker v-if="selectList.length!=0" mode="selector" :defaultVal="['女']" @confirm="onConfirmWater" ref="selectorOne"
		 :selectList="selectList" :themeColor='themeColor' :leftTopText='water'></w-picker>
		<w-picker v-if="selectList.length!=0" mode="selector" :defaultVal="['女']" @confirm="onConfirmUrinate" ref="selectorTwo"
		 :selectList="selectList" :themeColor='themeColor' :leftTopText='urinate'></w-picker>
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
				surplusValue: '',
				waterRecord: false,
				urinateRecord: false,
				surplusRecord: false,
				hasWaterRecord: false,
				hasUrinateRecord: false,
				hasSurplusRecord: false,
				currentTime: '',
				inputSurplus: '',
				isHide: false
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
				this.isHide = true;
			},
			onConfirmWater(e) {
				this.waterValue = e.result;
				const date = new Date();
				let Hours, Minutes = '';
				if (date.getHours().toString().length < 2) {
					Hours = '0' + date.getHours();
				} else {
					Hours = date.getHours();
				}
				if (date.getMinutes().toString().length < 2) {
					Minutes = '0' + date.getMinutes();
				} else {
					Minutes = date.getMinutes();
				}
				this.currentTime = Hours + ':' + Minutes;
				if (this.waterValue != '') {
					this.hasWaterRecord = true;
					this.waterRecord = true;
				} else {
					this.hasWaterRecord = false;
				}
			},
			onConfirmUrinate(e) {
				this.urinateValue = e.result;
				const date = new Date();
				let Hours, Minutes = '';
				if (date.getHours().toString().length < 2) {
					Hours = '0' + date.getHours();
				} else {
					Hours = date.getHours();
				}
				if (date.getMinutes().toString().length < 2) {
					Minutes = '0' + date.getMinutes();
				} else {
					Minutes = date.getMinutes();
				}
				this.currentTime = Hours + ':' + Minutes;
				if (this.urinateValue != '') {
					this.hasUrinateRecord = true;
					this.urinateRecord = true;
				} else {
					this.hasUrinateRecord = false;
				}
			},
			onConfirmSurplus(e) {
				this.surplusValue = this.inputSurplus;
				const date = new Date();
				let Hours, Minutes = '';
				if (date.getHours().toString().length < 2) {
					Hours = '0' + date.getHours();
				} else {
					Hours = date.getHours();
				}
				if (date.getMinutes().toString().length < 2) {
					Minutes = '0' + date.getMinutes();
				} else {
					Minutes = date.getMinutes();
				}
				this.currentTime = Hours + ':' + Minutes;
				if (this.surplusValue != '') {
					this.hasSurplusRecord = true;
					this.surplusRecord = true;
				} else {
					this.hasSurplusRecord = false;
				}
				this.isHide = false;	
			},
			showWaterBox() {
				if (this.hasWaterRecord == true) {
					this.waterRecord = !this.waterRecord;
				}
			},
			showUrinateBox() {
				if (this.hasUrinateRecord == true) {
					this.urinateRecord = !this.urinateRecord;
				}
			},
			showSurplusBox() {
				if (this.hasSurplusRecord == true) {
					this.surplusRecord = !this.surplusRecord;
				}
			},
			surplusInput(e) {
				this.inputSurplus = e.detail.value;
			},
			closeModel() {
				this.isHide = false;
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
		}

		.item {
			color: #80899c;
			background-color: #fff;

			.name {
				padding: 20rpx 0;
				font-size: 34rpx;
				position: relative;

				&::before {
					content: "";
					position: absolute;
					left: 0;
					bottom: 10rpx;
					width: 80rpx;
					height: 6rpx;
					background-color: #a69eff;
					border-radius: 3rpx;
				}

				.add-icon {
					display: inline-block;
					position: absolute;
					right: 0;
					width: 40rpx;
					height: 40rpx;

					&::before {
						content: '';
						position: absolute;
						right: 0;
						top: 18rpx;
						width: 39rpx;
						height: 39rpx;
						border-top: 3rpx solid #999999;
					}

					&::after {
						content: '';
						position: absolute;
						right: 19rpx;
						top: 0;
						width: 39rpx;
						height: 39rpx;
						border-right: 3rpx solid #999999;
					}
				}
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

			picker {
				font-size: 34rpx;
				color: red;
			}

			.result-box {
				display: flex;
				justify-content: space-between;

				.short-input-box {
					width: 280rpx;
					height: 70rpx;
					padding-left: 20rpx;
					margin-top: 20rpx;
					border: 2rpx solid #e0e4ee;
					font-size: 30rpx;
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

			.input-box-number {
				height: 70rpx;
				padding-left: 20rpx;
				margin: 20rpx 0;
				border: 2rpx solid #e0e4ee;
				font-size: 30rpx;
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

	.model-box {
		position: fixed;
		top: 200rpx;
		left: 50%;
		transform: translateX(-50%);
		width: 500rpx;
		padding: 30rpx 40rpx 0;
		background-color: #fff;
		z-index: 10;
		font-size: 30rpx;
		text-align: center;

		.surplus-input-box {
			width: 400rpx;
			border: 2rpx solid #e0e4ee;
			margin: 20rpx auto;
			position: relative;

			&::after {
				content: 'ml';
				position: absolute;
				top: 5rpx;
				right: 10rpx;
			}
		}

		.surplus-button-box {
			display: flex;
			justify-content: space-between;
			padding: 30rpx 0;

			.cancel {
				display: block;
				padding: 15rpx 80rpx;
				border: solid 1px #80899c;
			}

			.confirm {
				display: block;
				padding: 15rpx 80rpx;
				color: #fff;
				background-image: linear-gradient(0deg,
					#a69eff 0%,
					#ccc7ff 100%),
					linear-gradient(#ffffff,
					#ffffff);
				background-blend-mode: normal, normal;
			}
		}
	}
</style>
