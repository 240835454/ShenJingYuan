<template>
	<view class="page">
		<view class="content">
			<view class="box">
				<view class="item">
					<text class='name'>您的性别是</text>
					<view class="radio">
						<radio-group class='radio-group' @click='selectGender(value)'>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>男性</text>
							</label>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>女性</text>
							</label>
						</radio-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>您是否有感染病史？</text>
					<view class="radio">
						<radio-group class='radio-group' @click='selectGender(value)'>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>有</text>
							</label>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>无</text>
							</label>
						</radio-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>您的膀胱顺应性？</text>
					<view class="radio">
						<radio-group class='radio-group' @click='selectGender(value)'>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>正常或高</text>
							</label>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>低</text>
							</label>
						</radio-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>您的疾病病程？</text>
					<view class="radio">
						<radio-group class='radio-group' @click='selectGender(value)'>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>{{year}}</text>
							</label>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>>5年</text>
							</label>
						</radio-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>您是否大小便失禁？</text>
					<view class="radio">
						<radio-group class='radio-group' @click='selectGender(value)'>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>有</text>
							</label>
							<label class="radio">
								<radio :value="value" color='#fff' /><text>无</text>
							</label>
						</radio-group>
					</view>
				</view>
				<view class="footer">
					<text class='button'>确定提交</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value: 1,
				year: '<=5年'
			}
		},
		methods: {
			selectGender(e) {
				console.log(e);
			}
		}
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
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

				.radio {
					display: flex;
					align-items: center;
					padding: 30rpx 0;
					font-size: 30rpx;

					.radio-group {
						display: flex;

						label {
							width: 200rpx;
							padding: 0 60rpx 0 30rpx;
						}

						text {
							display: inline-block;
							padding-left: 20rpx;
						}
					}
				}
			}

			.footer {
				padding: 400rpx 0 60rpx 0;
				text-align: center;
				color: #fff;
				.button {
					padding: 20rpx 200rpx;
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
</style>
