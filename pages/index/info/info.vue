<template>
	<view class="page">
		<view class="box">
			<view class="content">
				<view class="title">
					<text>基本信息</text>
				</view>
			</view>
			<view>
				<view class="item-info" v-show='active'>
					<text class='name water'>姓名</text>
					<input type="text" :value="name" class='input-box' placeholder-class="phcolor" placeholder="请输入您的姓名" maxlength="5" />
					<text class='name'>年龄</text>
					<input type="text" :value="age" class='input-box pick' placeholder-class="phcolor" disabled placeholder="请选择您的年龄"
					 maxlength="5" @click="open" />
					<text class='name surplus'>电话</text>
					<input type="number" :value="phone" class='input-box' placeholder-class="phcolor" placeholder="请输入您的电话号码"
					 maxlength="5" />
					<view class="footer">
						<text class='button' @click='next'>
							下一页
						</text>
					</view>
				</view>
				<view class="item" v-show='!active'>
					<view class="item">
						<text class='name'>您的性别是</text>
						<view class="radio twoGroup">
							<radio-group class='radio-group'>
								<template v-for="(item,index) in gender">
									<label :key='index' class="radio" :class="index == gender.length-1 ? 'other': ''" @click='selectGender(index)'>
										<radio :value="value" color="#fff" /><text :class="genderIndex == index ? 'isChoose' : ''">{{item}}</text>
									</label>
								</template>
							</radio-group>
						</view>
					</view>
					<view class="item">
						<text class='name'>您是否有感染病史?</text>
						<view class="radio">
							<radio-group class='radio-group'>
								<template v-for="(item,index) in isInfect">
									<label :key='index' class="radio" @click='selectInfect(index)'>
										<radio :value="value" color="#fff" /><text :class="isInfectIndex == index ? 'isChoose' : ''">{{item}}</text>
									</label>
								</template>
							</radio-group>
						</view>
					</view>
					<view class="item">
						<text class='name'>您的膀胱顺应性?</text>
						<view class="radio">
							<radio-group class='radio-group'>
								<template v-for="(item,index) in bladder">
									<label :key='index' class="radio" @click='selectBladder(index)'>
										<radio :value="value" color="#fff" /><text :class="bladderIndex == index ? 'isChoose' : ''">{{item}}</text>
									</label>
								</template>
							</radio-group>
						</view>
					</view>
					<view class="item">
						<text class='name'>您的疾病病程?</text>
						<view class="radio">
							<radio-group class='radio-group'>
								<template v-for="(item,index) in course">
									<label :key='index' class="radio" @click='selectCourse(index)'>
										<radio :value="value" color="#fff" /><text :class="courseIndex == index ? 'isChoose' : ''">{{item}}</text>
									</label>
								</template>
							</radio-group>
						</view>
					</view>
					<view class="item">
						<text class='name'>您是否大小便失禁?</text>
						<view class="radio">
							<radio-group class='radio-group'>
								<template v-for="(item,index) in incontinence">
									<label :key='index' class="radio" @click='selectIncontinence(index)'>
										<radio :value="value" color="#fff" /><text :class="incontinenceIndex == index ? 'isChoose' : ''">{{item}}</text>
									</label>
								</template>
							</radio-group>
						</view>
					</view>
					<view class="item">
						<text class='name'>上传检查化验单?</text>
						<view class="imgList">
							<template v-for="(item,index) in imgList">
								<view class="image-item" :key='index'>
									<image :src="item" mode="aspectFit" class='image' @click="previewImg" :data-src='item'>
									</image>
									<image src="../../../static/icon_picture_del.png" mode="" class='clear-icon' @click='deleteImg(index)'></image>
								</view>
							</template>
							<view class="camera" @click="addImg" v-if="imgList.length<3">
								<image src="../../../static/camera.png" mode="" class=''></image>
							</view>
						</view>
					</view>
					<view class="footer">
						<text class='button' @click='confirm'>
							完成
						</text>
					</view>
				</view>
			</view>
		</view>
		<view class="mask">
		</view>
		<view class="hasComplete">
			<image src="../../../static/illustration_collect_complete.png" mode="aspectFit"></image>
			<text>基本信息采集完成!</text>
			<view class="button-box">
				<text class='button'>确定</text>
			</view>
		</view>
		<w-picker v-if="selectList.length!=0" mode="selector" @confirm="onConfirmAge" ref="selector" :selectList="selectList"
		 :themeColor='themeColor' :leftTopText='leftTopText'></w-picker>
	</view>
</template>

<script>
	import wPicker from "@/components/w-picker/w-picker.vue";
	export default {
		data() {
			return {
				leftTopText: '年龄',
				themeColor: '#a69eff',
				age: '',
				active: false,
				selectList: [{
					label: '22',
					value: '22'
				}, { 
					label: '23', 
					value: '23'
				}, {
					label: '24',
					value: '24'
				}],
				gender: ['男性', '女性', '其他'],
				isInfect: ['有', '无'],
				bladder: ['正常或高', '低'],
				course: ['<=5年', '>5年'],
				incontinence: ['有', '无'],
				genderIndex: -1,
				isInfectIndex: -1,
				bladderIndex: -1,
				courseIndex: -1,
				incontinenceIndex: -1,
				imgList: []
			}
		},
		methods: {
			open() {
				this.$refs.selector.show();
			},
			onConfirmAge(e) {
				this.age = e.result;
			},
			next() {
				this.active = false;
			},
			selectGender(e) {
				this.genderIndex = e;
			},
			selectInfect(e) {
				this.isInfectIndex = e;
			},
			selectBladder(e) {
				this.bladderIndex = e;
			},
			selectCourse(e) {
				this.courseIndex = e;
			},
			selectIncontinence(e) {
				this.incontinenceIndex = e;
			},
			previewImg(e) {
				let current = e.target.dataset.src;
				uni.previewImage({
					current: current,
					urls: this.imgList
				})
			},
			deleteImg(index) {
				this.imgList.splice(index, 1);
			},
			addImg() {
				uni.chooseImage({
					count: 3 - this.imgList.length,
					success: res => {
						this.imgList.push(res.tempFilePaths[0])
					},
					fail: err => {
						console.log(err);
					}
				})
			},
			confirm() {

			}
		},
		components: {
			wPicker
		}
	}
</script>

<style lang='less'>
	.page {
		position: relative;
	}

	.box {
		padding: 20rpx;

		.content {
			background-color: #fff;
			padding: 30rpx;

			.title {
				position: relative;
				display: block;
				font-size: 34rpx;
				color: #333333;

				&::before {
					content: "";
					position: absolute;
					left: 0;
					bottom: -10rpx;
					width: 80rpx;
					height: 6rpx;
					background-color: #a69eff;
					border-radius: 3rpx;
				}
			}
		}

		.item-info {
			color: #80899c;
			background-color: #fff;
			padding: 0 20rpx;

			.name {
				display: block;
				padding-left: 30rpx;
				font-size: 34rpx;
				position: relative;

				&::before {
					content: "";
					position: absolute;
					top: 25rpx;
					transform: translate(0, -50%);
					left: 10rpx;
					width: 4rpx;
					height: 20rpx;
					border-left: 4rpx solid #b2b9c9;
				}
			}

			.input-box {
				position: relative;
				height: 70rpx;
				padding-left: 20rpx;
				margin: 20rpx 0;
				border: 2rpx solid #e0e4ee;
				font-size: 30rpx;
			}

			.pick {
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

			.phcolor {
				font-size: 30rpx;
				color: #cccccc;
			}
		}

		.item {
			color: #80899c;
			background-color: #fff;
			padding-left: 10rpx;

			.imgList {
				padding: 30rpx 0 0 30rpx;
				background-color: #fff;
				display: flex;

				.image-item {
					position: relative;

					.image {
						width: 180rpx;
						height: 180rpx;
						padding-right: 30rpx;
					}

					.clear-icon {
						position: absolute;
						display: block;
						right: 15rpx;
						top: -15rpx;
						width: 36rpx;
						height: 36rpx;
					}
				}

				.camera {
					width: 180rpx;
					height: 180rpx;
					display: inline-block;
					border: 2rpx solid #e0e4ee;
					vertical-align: top;
					position: relative;

					image {
						position: absolute;
						top: 50%;
						left: 50%;
						transform: translate(-50%, -50%);
						width: 60rpx;
						height: 57rpx;
					}
				}
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
				position: relative;
				align-items: center;
				padding: 30rpx 0;
				font-size: 30rpx;
				color: #a6b5d5;

				.radio-group {
					display: flex;

					label {
						padding: 0 60rpx 0 30rpx;
					}

					text {
						padding-left: 20rpx;
					}
				}

				.isChoose {
					color: #80899c;
				}
			}

			.twoGroup {
				padding-bottom: 80rpx;
			}

			.other {
				position: absolute;
				padding: 20rpx 0;
				bottom: 20rpx;
			}

		}

		.footer {
			padding: 150rpx 0 60rpx 0;
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

	.hasComplete {
		position: absolute;
		top: 200rpx;
		left: 50%;
		width: 600rpx;
		transform: translateX(-50%);
		text-align: center;
		z-index: 10;
		background-color: #fff;

		image {
			width: 240rpx;
			margin: 0 auto;
		}

		text {
			display: block;
			font-size: 34rpx;
			color: #a69eff;
			letter-spacing: 1rpx;
		}
		
		.button-box{
			text-align: center;
			.button {
				display: inline-block;
				padding: 15rpx 170rpx;
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
