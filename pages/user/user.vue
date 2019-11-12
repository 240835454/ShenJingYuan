<template>
	<view class="page">
		<view class="header">
			<button class="" open-type="getUserInfo" @getuserinfo="wxGetUserInfo" withCredentials="true">未授权</button>
			<image :src="userInfo.avatarUrl" mode="" class='avatar'></image>
			<text class='nickName'>{{userInfo.nickName}}</text>
		</view>
		<view class="box">
			<view class="content">
				<view class="item" @click="enterUserInfo">
					<image src="../../static/icon_personal_data.png" mode="" class='icon'></image>
					<text>个人资料</text>
					<text class='right'>请完善资料</text>
				</view>
				<view class="item" @click='enterMessage'>
					<image src="../../static/icon_personal_message.png" mode="" class='icon'></image>
					<text>消息通知</text>
					<text class='right'>消息通知</text>
				</view>
				<view class="item" @click='enterChangePhone'>
					<image src="../../static/icon_personal_phone.png" mode="" class='short-icon'></image>
					<text>修改手机</text>
					<text class='right' v-text="hasPhone ? '修改手机' : '请绑定手机号'"></text>
				</view>
				<view class="last-item">
					<image src="../../static/icon_personal_log_out.png" mode="" class='middle-icon'></image>
					<text>退出登录</text>
					<text class='right'></text>
				</view>
				<view class="mask" v-show="isHide">
				</view>
				<view class="bind-phone-box" v-show="isHide">
					<text class='title'>绑定手机号</text>
					<input type="number" value="" class='input-box' placeholder-class="phcolor" placeholder="请输入您的手机号码" maxlength="11" />
					<input type="number" value="" class='input-box' placeholder-class="phcolor" placeholder="输入验证码" maxlength="11" />
					<text class='verify-code'>获取验证码</text>
					<view class="button-box">
						<text class='cancel' @click='close'>取消</text>
						<text class='submit'>确定</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: {},
				hasPhone: false,
				bindPhone: false,
				isHide: false,
			}
		},
		onLoad() { 
			this.wxGetUserInfo()
		},
		methods: {
			wxGetUserInfo: function(res) {
				console.log(res);
				if (!res.detail.iv) {
					uni.showToast({
						title: "您取消了授权,登录失败",
						icon: "none"
					});
					return false;
				}
				console.log(res.detail);
				this.userInfo = res.detail.userInfo;
			},
			enterUserInfo() {
				uni.navigateTo({
					url: 'userInfo'
				})
			},
			enterMessage() {
				uni.navigateTo({
					url: 'message'
				})
			},
			enterChangePhone() {
				if (this.hasPhone) {
					uni.navigateTo({
						url: 'changePhone'
					})
				} else {
					this.isHide = true;
				}
			},
			close(){
				this.isHide = false;
			}
		}
	}
</script>

<style lang="less">
	.header {
		position: relative;
		height: 330rpx;
		padding: 45rpx 0;
		background-color: #fff;
		text-align: center;

		button {
			width: 180rpx;
			height: 180rpx;
			line-height: 180rpx;
			border: 0;
			border-radius: 50%;
			pointer-events: auto;

			&::after {
				border: none;
			}
		}

		.avatar {
			position: absolute;
			top: 45rpx;
			left: 50%;
			transform: translate(-50%, 0);
			width: 180rpx;
			height: 180rpx;
			border-radius: 50%;
			pointer-events: none;
		}

		.nickName {
			display: block;
			padding-top: 40rpx;
			color: #333333;
			font-size: 36rpx;
		}
	}

	.box {
		padding: 30rpx 20rpx 20rpx;

		.content {
			border-radius: 10rpx;
			position: relative;

			.item {
				display: flex;
				align-items: center;
				padding: 40rpx;
				background-color: #fff;
				font-size: 30rpx;
				color: #666;
				border-bottom: 1rpx solid rgba(128, 137, 156, 0.2);

				&:nth-child(3) {
					border: none;
				}

				.icon {
					flex: 0 0 40rpx;
					height: 40rpx;
					padding-right: 30rpx;
				}

				.short-icon {
					flex: 0 0 29rpx;
					height: 40rpx;
					text-align: center;
					padding: 0 38rpx 0 8rpx;
				}

				.middle-icon {
					.icon;
					height: 36rpx;
				}

				.right {
					position: absolute;
					right: 80rpx;
					font-size: 28rpx;
					color: #b3b3b3;

					&::after {
						border: solid #e5e5e5;
						border-width: 2rpx 2rpx 0 0;
						content: " ";
						top: 50%;
						right: -30rpx;
						position: absolute;
						width: 14rpx;
						height: 14rpx;
						-webkit-transform: translateY(-50%) rotate(45deg);
						transform: translateY(-50%) rotate(45deg);
					}
				}
			}

			.last-item {
				.item;
				margin-top: 30rpx;
				border: none;
				border-radius: 10rpx;
			}

			.bind-phone-box {
				position: absolute;
				top: -120rpx;
				left: 50%;
				transform: translateX(-50%);
				width: 600rpx;
				height: 540rpx;
				background-color: #fff;
				font-size: 34rpx;
				z-index: 10;

				.title {
					display: block;
					padding: 48rpx 0 60rpx;
					text-align: center;
				}

				.input-box {
					width: 500rpx;
					height: 90rpx;
					padding-left: 20rpx;
					margin-top: 20rpx;
					font-size: 30rpx;
					background-color: #f7f7f7;
					margin: 20rpx auto 0;
				}
				
				.verify-code{
					position: absolute;
					top: 295rpx;
					right: 60rpx;
					display: block;
					padding: 16rpx 20rpx;
					background-color: #fff;
					font-size: 24rpx;
				}

				.phcolor {
					color: #b3b3b3;
				}

				.button-box {
					display: flex;
					justify-content: space-between;
					padding: 60rpx 40rpx;
					background-color: #fff;
					.submit {
						padding: 16rpx 90rpx;
						color: #fff;
						background-image: linear-gradient(0deg,
							#a69eff 0%,
							#ccc7ff 100%),
							linear-gradient(#ffffff,
							#ffffff);
						background-blend-mode: normal,
							normal;
					}
					.cancel{
						padding: 15.5rpx 89.5rpx;
						color: #80899c;
						background-color: #fff;
						border: solid 1px #80899c;
					}
				}
			}
		}
	}
</style>
