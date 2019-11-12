<template>
	<view class="page">
		<view class="box">
			<view class="content">
				<view class="info-item-phone" :key='index'>
					<text class='name'>
						新手机号码
					</text>
					<input type="number" value="" class='input-box' placeholder-class="phcolor" placeholder="请输入新手机号码" maxlength="11" />
				</view>
				<view class="info-item-phone" :key='index'>
					<text class='name'>
						手机验证码
					</text>
					<view class="verify-code">
						<input type="number" value="" class='short-input-box' placeholder-class="phcolor" placeholder="请输入验证码" maxlength="11" />
						<view class="">
							<text class='code'>获取验证码</text>
						</view>
					</view>
				</view>
				<view class="footer">
					<text class='button'>确定</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		}
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
	}

	.box {
		padding: 20rpx;
	}

	.content {
		background-color: #fff;
		color: #80899c;

		.info-item-phone {
			padding: 40rpx 30rpx 0;
			font-size: 30rpx;
			background-color: #fff;

			.name {
				display: block;
				padding-left: 30rpx;
				font-size: 34rpx;
				position: relative;

				&::before {
					content: "";
					position: absolute;
					top: 25rpx;
					left: 0;
					transform: translate(0, -50%);
					width: 4rpx;
					height: 20rpx;
					border-left: 4rpx solid #b2b9c9;
				}
			}

			.input-box {
				height: 70rpx;
				padding-left: 20rpx;
				margin-top: 20rpx;
				border: 2rpx solid #e0e4ee;
				font-size: 30rpx;
			}
			
			.verify-code{
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding-bottom: 20rpx;
				margin-top: 20rpx;
				.short-input-box{
					width: 380rpx;
					height: 70rpx;
					border: 2rpx solid #e0e4ee;
					padding-left: 20rpx;
				}
				.code{
					display: block;
					width: 200rpx;
					padding: 15rpx;
					text-align: center;
					border: 2rpx solid #a69eff;
					border-radius: 35rpx;
					color: #a69eff;
					font-size: 30rpx;
				}
			}

			.phcolor {
				color: #cccccc;
			}
		}

		.footer {
			padding: 500rpx 0 80rpx;
			text-align: center;
			background-color: #fff;
			.button {
				padding: 20rpx 240rpx;
				color: #fff;
				background-image: linear-gradient(0deg,
					#a69eff 0%,
					#ccc7ff 100%),
					linear-gradient(#ffffff,
					#ffffff);
				background-blend-mode: normal,
					normal;
			}
		}
	}
</style>
