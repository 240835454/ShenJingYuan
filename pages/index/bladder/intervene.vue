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
			<view class="box" v-show='activeIndex == 0'>
				<view class="item">
					<text class='name'>饮水计划</text>
					<view class="checkBox">
						<checkbox-group @click='waterPlan'>
							<label class='checkBox-item'>
								<checkbox value="cb" :checked="waterPlanState" color="#FFCC33" style="transform:scale(0.7)" /><text :class="waterPlanState ? 'isChoose' : ''">每天饮水量控制在1500-2000ml,每次不超过400ml,入睡前3h尽量不饮水</text>
							</label>
						</checkbox-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>排尿计划</text>
					<view class="checkBox">
						<checkbox-group @click='urinatePlan'>
							<label class='checkBox-item'>
								<checkbox value="cb" :checked="urinatePlanState" color="#FFCC33" style="transform:scale(0.7)" /><text :class="urinatePlanState ? 'isChoose' : ''">Q4h～6h（白天)夜间排空膀胱[脊髓损伤患者不推荐使用Crede手法辅助排尿</text>
							</label>
						</checkbox-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>清洁间歇导尿</text>
					<view class="radio">
						<radio-group class='radio-group'>
							<template v-for="(item,index) in cleanList">
								<label class="radio-item" :key='index' @click='selectRadio(index)'>
									<radio :value="value" color='#fff' /><text :class="cleanIndex == index ? 'isChoose' : ''">{{item}}</text>
								</label>
							</template>
						</radio-group>
					</view>
				</view>
				<view class="footer">
					<text class='button'>
						确定
					</text>
				</view>
			</view>
			<view class="box" v-show='activeIndex == 1'>
				<view class="item">
					<text class='name'>(多选)预防泌尿系感染</text>
					<view class="checkBox'">
						<checkbox-group class=''>
							<template v-for="(item,index) in preventList">
								<label class='checkBox-item' :key='index' @click='preventIndex(index)'>
									<checkbox value="cb" :checked="false" color="#FFCC33" style="transform:scale(0.7)" /><text :class="item.active ? 'isChoose' : ''">{{item.text}}</text>
								</label>
							</template>
						</checkbox-group>
					</view>
				</view>
				<view class="footer">
					<text class='button'>
						确定
					</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				TabList: [
					'清洁间歇导尿推荐方案',
					'预防泌尿系感染'
				],
				activeIndex: 0,
				cleanList: [
					'(q4-6h）自行排尿少于100ml或残余尿量高于300ml时',
					'(q6h）自行排尿 > 100ml，或残余尿量 < 300ml时',
					'(q8h）自行排尿超过200ml，或残余尿量低于200ml时，每8小时导尿一次',
					'(停止导尿）当残余尿 < 100 mL，即为膀胱容量的 10％-20％，连续监测残余量7天，残余量均 < 100 mL，则可停止间歇导尿',
				],
				preventList: [{
						text: '注意手卫生，导尿前，导尿后严格执行七步洗手法',
						active: false
					},
					{
						text: '导尿术护理 （每天）',
						active: false
					},
					{
						text: '会阴部、尿道口的护理 （每天），用温水清洁会阴保持会阴区皮肤清洁干燥',
						active: false
					},
					{
						text: '勤换内裤，穿棉质、透气的内裤',
						active: false
					},
					{
						text: '保持肛门周围清洁干燥',
						active: false
					}

				],
				waterPlanState: true,
				urinatePlanState: false,
				cleanIndex: -1
			}
		},
		methods: {
			changeTab(e) {
				this.activeIndex = e;
			},
			radioChange(e) {
				console.log(e);
			},
			waterPlan(e) {
				this.waterPlanState = !this.waterPlanState;
			},
			urinatePlan(e) {
				this.urinatePlanState = !this.urinatePlanState;
			},
			selectRadio(e) {
				this.cleanIndex = e;
			},
			preventIndex(e) {
				this.preventList[e].active = !this.preventList[e].active;
			}
		},
	}
</script>

<style lang="less">
	page {
		height: 100%;
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
				left: 50%;
				transform: translate(-50%, 0);
				bottom: 15rpx;
				border-bottom: 6rpx solid #a69eff;
				border-radius: 5rpx;
			}
		}
	}

	.content {
		padding: 20rpx;
		font-family: PingFang-SC-Medium;

		.box {
			padding: 40rpx 20rpx;
			background-color: #fff;

			.item {
				color: #80899c;

				.name {
					padding-left: 30rpx;
					font-size: 34rpx;
					position: relative;

					&::before {
						content: "";
						position: absolute;
						top: 35%;
						left: 10rpx;
						width: 4rpx;
						height: 20rpx;
						border-left: 4rpx solid #b2b9c9;
					}
				}

				.checkBox {
					display: flex;
					padding: 20rpx;
					font-size: 30rpx;
					color: #a6b5d5;

					.checkBox-item {
						display: flex;
						align-items: center;
						padding: 10rpx 0;
					}

					text {
						display: block;
						padding-left: 20rpx;
					}
				}

				.radio {
					display: flex;
					padding: 30rpx;
					font-size: 30rpx;
					color: #a6b5d5;

					.radio-item {
						display: flex;
						align-items: center;
						padding-bottom: 30rpx;
					}

					text {
						display: block;
						padding-left: 20rpx;
					}
				}

				.isChoose {
					color: #80899c;
				}
			}

			.footer {
				padding: 40rpx 0 20rpx 0;
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
	}


	radio {
		border-radius: 50%;
		width: 40rpx;
		height: 40rpx;
		border: 1rpx solid #a6b5d5;
		font-size: 0;
	}

	radio .wx-radio-input {
		border-radius: 50%;
		width: 40rpx;
		height: 40rpx;
		border: none;
	}

	radio .wx-radio-input.wx-radio-input-checked::before {
		content: "";
		width: 30rpx;
		height: 30rpx;
		background-color: #a6b5d5;
		border-radius: 50%;
	}

	checkbox {
		border-radius: 50%;
		width: 60rpx;
		height: 60rpx;
	}

	checkbox .wx-checkbox-input {
		border-radius: 50%;
		width: 60rpx;
		height: 60rpx;
	}

	checkbox .wx-checkbox-input.wx-checkbox-input-checked {
		border: 1rpx solid #a6b5d5;
	}

	checkbox .wx-checkbox-input.wx-checkbox-input-checked::before {
		content: "";
		width: 40rpx;
		height: 40rpx;
		background-color: #a6b5d5;
		border: 1rpx solid #d2ddf5;
		;
		border-radius: 50%;
		text-align: center;
	}
</style>
