<template>
	<view class="page">
		<view class="calendar">
			<uni-calendar :insert="true" @change="change" :selected="selected" ref="calendar"></uni-calendar>
		</view>
		<view class="content">
			<text @click='enterRecord' :class="hasRecord ? 'hasRecord' : 'button'" v-text="hasRecord ? '已记录': '开始记录'"></text>
		</view>
	</view>
</template>

<script>
	import {
		uniCalendar
	} from "@/components/uni-calendar/uni-calendar"
	export default {
		components: {
			uniCalendar
		},
		data() {
			return {
				selected: [{
					date: '2019-11-21',
					data: {
						all: true,
					}
				}, {
					date: '2019-11-22',
					data: {
						all: true,
					}
				}, {
					date: '2019-11-24',
					data: {
						all: true,
					}
				}, {
					date: '2019-11-25',
					data: {
						all: true,
					}
				}],
				infoList: [{
						name: '清洁间歇导尿推荐方案',
						value: '已完成'
					},
					{
						name: '预防泌尿系感染',
						value: '未完成'
					}
				],
				hasRecord: false
			};
		},
		methods: {
			change(e) {
				console.log(e.clockinfo.have);
				e.clockinfo.have ? this.hasRecord = true : this.hasRecord = false;
				console.log(this.hasRecord)
			},
			confirm(e) {
				console.log(e);
			},
			enterProject(index) {
				uni.navigateTo({
					url: 'intervene'
				})
			},
			enterRecord(){
				uni.navigateTo({
					url: 'record'
				})
			}
		}
	};
</script>

<style lang="less">
	page {
		height: 100%;
		background-repeat: no-repeat;
		background-size: cover;
		background-image: url('~@/static/背景.png');
	}

	.calendar {
		padding: 100upx 20upx 0;
		position: relative;

		&::before {
			content: "";
			position: absolute;
			top: 70upx;
			left: 25%;
			width: 30upx;
			height: 60upx;
			border: 5upx solid #c4beff;
			border-radius: 20upx;
			background-color: #fff;
			z-index: 2;
		}

		&::after {
			content: "";
			position: absolute;
			top: 70upx;
			right: 25%;
			width: 30upx;
			height: 60upx;
			border: 5upx solid #c4beff;
			border-radius: 20upx;
			background-color: #fff;
			z-index: 2;
		}
	}

	.content {
		padding: 40rpx 0 120rpx;
		background-color: #fff;
		margin: 0 20rpx;
		text-align: center;
		.button {
			padding: 24rpx 135rpx;
			font-size: 34rpx;
			color: #fff;
			background-image: linear-gradient(0deg,
				#a69eff 0%,
				#ccc7ff 100%),
				linear-gradient(#ffffff,
				#ffffff);
			background-blend-mode: normal,
				normal;
			border-radius: 60rpx;
		}
		
		.hasRecord{
			padding: 24rpx 135rpx;
			font-size: 34rpx;
			background-color: #fff;
			border: solid 2rpx #a69eff;
			border-radius: 60rpx;
			color: #a69eff;
			letter-spacing: 10rpx;
		}
	}
</style>
