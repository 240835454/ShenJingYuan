<template>
	<view class="page">
		<view class="calendar">
			<uni-calendar :insert="true" @change="change" :selected="selected" ref="calendar"></uni-calendar>
		</view>
		<view class="content">
			<template v-for='(item,index) in infoList'>
				<view class="info-item" :key='index' @click='enterProject(index)'>
					<text class='name'>
						{{item.name}}
					</text>
					<text class='value' :class="item.value == '已完成' ? 'complete' : ''">
						{{item.value}}
					</text>
				</view>
			</template>
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
						single: false
					}
				}, {
					date: '2019-11-22',
					data: {
						all: false,
						single: true
					}
				}, {
					date: '2019-11-24',
					data: {
						all: true,
						single: false
					}
				}, {
					date: '2019-11-25',
					data: {
						all: true,
						single: false
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
			};
		},
		methods: {
			change(e) {
				console.log(e);
			},
			toClick(e) {
				console.log(e);
			},
			confirm(e) {
				console.log(e);
			},
			enterProject(index){
				uni.navigateTo({
					url:'intervene'
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
	
	.content{
		position: relative;
		padding-bottom: 120rpx;
		margin: 0 20rpx;
		background-color: #fff;
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
		&:last-child{
			border-bottom: 1rpx solid #e6e7eb;
		}

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
		
		.complete{
			color: #a69eff;
		}
	}
</style>
