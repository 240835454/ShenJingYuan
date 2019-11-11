<template>
	<view class="page">
		<view class="box">
			<template v-for="(item,index) in messageList">
				<view :key='index' class='item'>
					<view class="flex">
						<text class='title' :class="item.state == 1 ? 'active' : 'hasRead'">{{item.title}}</text>
						<text class='date' :class="item.state == 1 ? '' : 'hasRead'">{{item.date}}</text>
					</view>
					<text class='text' :class="item.state == 1 ? '' : 'hasRead'">
						{{item.text}}
					</text>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				messageList: [
					{
						title: '本周健康测试',
						text: '本周健康测试开始啦~动手填写本周健康情况，系统将为您评估本周膀胱管理危险评估等级。',
						date: '21:53',
						state: '1',
					},
					{
						title: '本周健康测试',
						text: '本周健康测试开始啦~动手填写本周健康情况，系统将为您评估本周膀胱管理危险评估等级。',
						date: '21:53',
						state: '2',
					}
				]
			}
		}
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
	}
	
	.box{
		padding: 20rpx;
	}
	
	.item{
		background-color: #fff;
		padding: 30rpx 30rpx 40rpx;
		margin-bottom: 30rpx;
		position: relative;
		.flex{
			display: flex;
			justify-content: space-between;
			.title{
				font-size: 34rpx;
				color: #333333;
				letter-spacing: 1rpx;
			}
			.date{
				font-size: 26rpx;
				color: #808080;
			}
			.active{
				&::before{
					content: "";
					position: absolute;
					top: 10rpx;
					left: 10rpx;
					width: 14rpx;
					height: 14rpx;
					background-color: #a69eff;
					border-radius: 50%;
				}
			}
			.hasRead{
				color: #cccccc;
			}
		}
		.text{
			font-size: 28rpx;
			color: #808080;
		}
		.hasRead{
			color: #cccccc;
		}
	}
	
</style>
