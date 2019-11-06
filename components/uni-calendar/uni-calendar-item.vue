<template>
	<view>
		<block v-for="(weeks, week) in canlender.weeks" :key="week">
			<view class="uni-calender__body-date-week">
				<block v-for="(day, index) in weeks" :key="index">
					<view :class="{
              'uni-calender__disable': canlender.month !== day.month || day.disable,
              'uni-calender__date-current':
                ((day.date == canlender.date && !day.checked) || day.multipleBegin || day.multipleEnd) && canlender.month == day.month && !day.disable,
              'uni-calender__lunar': lunar,
              'uni-calender__active': !day.isDay,
              'uni-calender__is-day': day.isDay,
              'uni-calender__multiple': day.multipleBegin || day.multipleEnd,
              'uni-calender__multiple-box': day.checked
            }"
					 class="uni-calender__date" @tap="selectDays(week, index, canlender.month === day.month, day.disable, canlender.lunar)">
						<view class="uni-calender__circle-box" :class="day.clockinfo.data.all ? 'all' : (day.clockinfo.data.single ? 'single' : '')">
							{{ day.date }}
							<view v-if="lunar" class="uni-calender__lunar">{{ day.lunar }}</view>
							<view v-if="day.have" :class="day.clockinfo.data.all ? 'uni-calender__data-circle' : 'uni-calender__data-circle_single'" />
							<view v-if="day.have && !lunar" class="uni-calender__lunar">{{ day.clockinfo.info }}</view>
						</view>
						<view :class="{ 'uni-calender_check': day.checked, 'calender_check-begin': day.multipleBegin, 'calender_check-end': day.multipleEnd }"
						 class="uni-calender_check-bg" />
					</view>
				</block>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		name: 'UniCalendarItem',
		props: {
			/**
			 * 当前日期
			 */
			canlender: {
				type: null,
				default: () => {
					return {}
				}
			},
			lunar: {
				type: Boolean,
				default: false
			}
		},
		data() {
			return {}
		},
		created() {
			console.log(this.canlender)
		},
		methods: {
			selectDays(week, index, ischeck, isDay, lunar) {
				this.$emit('selectDays', {
					week,
					index,
					ischeck,
					isDay,
					lunar
				})
			}
		}
	}
</script>

<style lang="scss">
	.uni-calender__body-date-week {
		display: flex;
		width: 100%;
		// border-bottom: 1px #f5f5f5 solid;

		&:last-child {
			border: none;
		}

		// 日期的样式
		.uni-calender__date {
			position: relative;
			width: 100%;
			text-align: center;
			display: flex;
			justify-content: center;
			align-items: center; 
			color: #80899c;
			background: #fff;
			font-size: 28rpx;
			// line-height: 100upx;
			box-sizing: border-box;
			padding: 10upx 0;
			line-height: 1.5;
			z-index: 2;

			.uni-calender__lunar {
				font-size: 20upx;
				color: #000;
				line-height: 1.2;
			}

			.uni-calender__circle-box {
				display: flex;
				flex-direction: column;
				justify-content: center;
				align-items: center;
				width: 80upx;
				height: 80upx;
				flex-shrink: 0;
				border-radius: 10upx;
				// transition: all 0.2s;
				line-height: 1.2;
			}

			&.uni-calender__lunar {
				// 			padding: 20upx 0;
				// 			line-height: 1.5;
			}

			// 本月禁止的样式
			&.uni-calender__disable {
				color: #f1f1f1;
				visibility: hidden;  // 隐藏非当月日期
				.uni-calender__lunar {
					color: #f1f1f1;
				}
			}

			// &.uni-calender__is-day {
			// 	color: #fd2e32;
			// }

			&.uni-calender__is-day {
				// color: #fd2e32;
				position: relative;
				color: #80899c;
				&::after{
					content: "";
					position: absolute;
					bottom: 0;
					width: 8upx;
					height: 8upx;
					background-color: #a69eff;
					border-radius: 50%;
				}

				.uni-calender__lunar {
					color: #fd2e32;
				}
			}

			// 当前选中
			&.uni-calender__date-current {
				// background: #000;
				color: #fff;
				box-sizing: border-box;

				.uni-calender__circle-box {
					color: #a69eff;
					border: 1upx solid #a69eff;
					border-radius: 50%;
					width: 70upx;
					height: 70upx;
					box-sizing: border-box;
					// background: #fd2e32;
					// background-image: linear-gradient(0deg,
					// 	#a69eff 0%,
					// 	#ccc7ff 100%),
					// 	linear-gradient(#ff67b2,
					// 	#ff67b2);
					// background-blend-mode: normal,
					// 	normal;
					border-radius: 50%;
				}

				&.uni-calender__active {
					color: #fff;

					.uni-calender__circle-box {
						// background: red;
						border: 1upx solid #a69eff;
						border-radius: 50%;
						box-sizing: border-box;
					}
				}

				&.uni-calender__multiple {
					.uni-calender__circle-box {
						border-radius: 50%;
						background: #fd2e32;
					}
				}

				.uni-calender__lunar {
					color: #fff;
				}
			}

			&.uni-calender__multiple-box {
				color: #fff;

				.uni-calender__lunar {
					color: #fff;
				}

				// background: skyblue;
			}

			.uni-calender__data-circle {  // 选中 日期的背景颜色  全完成
				position: absolute;
				// bottom: 10rpx;
				// top: 5upx;
				// right: 5upx;
				// margin: auto;
				width: 70rpx;
				height: 70rpx;
				border-radius: 50%;
					background-image: linear-gradient(0deg, 
						#a69eff 0%, 
						#ccc7ff 100%), 
					linear-gradient(
						#ff67b2, 
						#ff67b2);
					background-blend-mode: normal, 
						normal;
				// border: 1px #fff solid;
				z-index: -1;
			}
			
			.uni-calender__data-circle_single{    // 选中  日期的背景颜色  只完成一个
				position: absolute;
				width: 70rpx;
				height: 70rpx;
				border: 2upx solid #a69eff;
				border-radius: 50%;
			}
			
			.all{     
				color: #fff !important;
			}
			
			.single{
				color: #a69eff;
			}

			.uni-calender_check-bg {
				position: absolute;
				top: 10upx;
				bottom: 10upx;
				// width: 100%;
				left: 0;
				right: 0;
				z-index: -1;

				&.uni-calender_check {
					background: #ffd3d3;
				}

				&.calender_check-begin {
					left: 20upx;
					border-top-left-radius: 100upx;
					border-bottom-left-radius: 100upx;
				}

				&.calender_check-end {
					right: 20upx;
					border-top-right-radius: 100upx;
					border-bottom-right-radius: 100upx;
				}
			}
		}
	}
</style>
