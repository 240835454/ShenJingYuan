<template>
	<view class="page">
		<view class="content">
			<view class="box">
				<view class="item">
					<text class='name'>姓名</text>
					<input type="text" value="" class='input-box' placeholder-class="phcolor" placeholder="请输入姓名" maxlength="10" />
				</view>
				<view class="item">
					<text class='name'>年龄</text>
					<input type="text" :value="age" class='input-box select-icon' placeholder-class="phcolor" disabled placeholder="请选择年龄"
					 maxlength="5" @click="open" />
				</view>
				<view class="item">
					<text class='name'>性别</text>
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
					<text class='name'>是否有感染病史</text>
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
					<text class='name'>膀胱顺应性</text>
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
					<text class='name'>疾病病程</text>
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
					<text class='name'>大小便失禁</text>
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
					<text class='name'>检查化验单</text>
					<view class="imgList">
						<template v-for="(item,index) in imgList">
							<image :src="item" mode="" :key='index' class='image'></image>
						</template>
					</view>
				</view>
				<view class="footer">
					<text class='button'>确定修改</text>
				</view>
			</view>
		</view>
		<w-picker v-if="selectList.length!=0" mode="selector" @confirm="onConfirm" ref="selector" :selectList="selectList"
		 :themeColor='themeColor' :leftTopText='leftTopText'></w-picker>
	</view>
</template>

<script>
	import wPicker from "@/components/w-picker/w-picker.vue";
	export default {
		data() { 
			return {
				value: 1,
				year: '<=5年',
				selectList: [{
						label: '21',
						value: '21'
					},
					{
						label: '22',
						value: '22'
					}, {
						label: '23',
						value: '23'
					}
				],
				themeColor: '#a69eff',
				leftTopText: '年龄',
				age: '',
				imgList: [
					'http://img0.imgtn.bdimg.com/it/u=1563847232,2166245740&fm=26&gp=0.jpg',
					'http://img0.imgtn.bdimg.com/it/u=1563847232,2166245740&fm=26&gp=0.jpg',
					'http://img0.imgtn.bdimg.com/it/u=1563847232,2166245740&fm=26&gp=0.jpg'
				],
			}
		},
		methods: {
			selectGender(e) {
				console.log(e);
			},
			open() {
				this.$refs.selector.show();
			},
			onConfirm(e) {
				this.age = e.result
			}
		},
		components: {
			wPicker
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

				.input-box {
					height: 70rpx;
					padding-left: 20rpx;
					margin: 20rpx 0;
					border: 2rpx solid #e0e4ee;
					font-size: 30rpx;
				}

				.select-icon {
					position: relative;

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

				.imgList {
					padding: 30rpx 0 0 30rpx;
					background-color: #fff;

					.image {
						width: 180rpx;
						height: 180rpx;
						padding-right: 30rpx;
					}
				}

				.phcolor {
					font-size: 30rpx;
					color: #cccccc;
				}

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
				padding: 60rpx 0;
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
