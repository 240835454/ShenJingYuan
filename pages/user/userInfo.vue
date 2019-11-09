<template>
	<view class="page">
		<view class="content">
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
					检查化验单
				</text>
				<text class='value'>
					&nbsp;
				</text>
			</view>
			<view class="imgList">
				<template v-for="(item,index) in imgList">
					<image :src="item" mode="" :key='index' class='image'></image>
				</template>
			</view>
			<view class="footer">
				<text class='button' @click='enterChangeInfo'>
					修改资料
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
				imgList:[
					'http://img0.imgtn.bdimg.com/it/u=1563847232,2166245740&fm=26&gp=0.jpg',
					'http://img0.imgtn.bdimg.com/it/u=1563847232,2166245740&fm=26&gp=0.jpg',
					'http://img0.imgtn.bdimg.com/it/u=1563847232,2166245740&fm=26&gp=0.jpg'
				],
				infoList: [
					{
						name: '姓名',
						value: '陈臻William'
					},
					{
						name: '年龄',
						value: 25
					},
					{
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
			enterChangeInfo(){
				uni.navigateTo({
					url: 'changeInfo'
				})
			}
		}
	}
</script>

<style lang='less'>
	page {
		height: 100%;
		background-color: #f9fafd;
	}
	
	.content {
		padding: 20rpx 20rpx 40rpx;
		color: #80899c;

		.box {
			background-color: #fff;
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

		.info-item {
			display: flex;
			justify-content: space-between;
			align-items: center;
			position: relative;
			padding: 40rpx 80rpx;
			font-size: 30rpx;
			border-top: 1rpx solid #e6e7eb;
			background-color: #fff;
			&:first-child{
				border: none;
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
		}
		
		.imgList{
			padding-left: 80rpx;
			background-color: #fff;
			.image{
				width: 180rpx;
				height: 180rpx;
				padding-right: 30rpx;
			}
		}

		.footer {
			padding: 80rpx 0;
			text-align: center;
			background-color: #fff;
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
