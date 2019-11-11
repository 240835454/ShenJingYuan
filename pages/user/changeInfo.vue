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
					<text class='name'>是否有感染病史</text>
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
					<text class='name'>膀胱顺应性</text>
					<view class="radio">
						<radio-group class='radio-group'>
							<template v-for="(item,index) in bladder">
								<label :key='index' class="radio"  @click='selectBladder(index)'>
									<radio :value="value" color="#fff" /><text :class="bladderIndex == index ? 'isChoose' : ''">{{item}}</text>
								</label>
							</template>
						</radio-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>疾病病程</text>
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
					<text class='name'>大小便失禁</text>
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
					<text class='name'>检查化验单</text>
					<view class="imgList">
						<template v-for="(item,index) in imgList">
							<view class="image-item" :key='index'>
								<image :src="item" mode=""  class='image' @click="previewImg" :data-src='item'>
								</image>
								<image src="../../static/icon_picture_del.png" mode="" class='clear-icon' @click='deleteImg(index)'></image>
							</view>
						</template>
						<view class="camera" @click="addImg" v-if="imgList.length<3">
							<image src="../../static/camera.png" mode="" class=''></image>
						</view>
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
				gender: ['男性','女性','其他'],
				isInfect: ['有','无'],
				bladder: ['正常或高','低'],
				course: ['<=5年','>5年'],
				incontinence: ['有','无'],
				genderIndex: -1,
				isInfectIndex: -1,
				bladderIndex: -1,
				courseIndex: -1,
				incontinenceIndex: -1,
				themeColor: '#a69eff',
				leftTopText: '年龄',
				age: '',
				imgList:[
					'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1573461179335&di=743743eaa389cb83a9c0766e93f9e6d4&imgtype=0&src=http%3A%2F%2Fi0.hdslb.com%2Fbfs%2Farchive%2F6491c748440e49a77286875012fcdf98a4a419f0.jpg',
					'http://i.caigoubao.cc/619923/eks-7.jpg'
				],
			}
		},
		methods: {
			selectGender(e) {
				this.genderIndex = e;
			},
			selectInfect(e){
				this.isInfectIndex = e;
			},
			selectBladder(e){
				this.bladderIndex = e;
			},
			selectCourse(e){
				this.courseIndex = e; 
			},
			selectIncontinence(e){
				this.incontinenceIndex = e;
			},
			previewImg(e){
				let current = e.target.dataset.src;
				uni.previewImage({
					current: current,
					urls: this.imgList
				})
			},
			deleteImg(index){
				this.imgList.splice(index,1);
			},
			addImg(){
				uni.chooseImage({
					count:3-this.imgList.length,
					success:res=>{
						this.imgList.push(res.tempFilePaths)
					},
					fail: err=>{
						console.log(err);
					}
				})
			},
			open() {
				this.$refs.selector.show();
			},
			onConfirm(e) {
				this.age = e.result;
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
					display: flex;
				.image-item{
					position: relative;
					.image {
						width: 180rpx;
						height: 180rpx;
						padding-right: 30rpx;
					}
					.clear-icon{
						position: absolute;
						display: block;
						right: 15rpx;
						top: -15rpx;
						width: 36rpx;
						height: 36rpx;
					}
				}
					
					.camera{
						width: 180rpx;
						height: 180rpx;
						display: inline-block;
						border: 2rpx solid #e0e4ee;
						vertical-align: top;
						position: relative;
						image{
							position: absolute;
							top: 50%;
							left: 50%;
							transform: translate(-50%,-50%);
							width: 60rpx;
							height: 57rpx;
						}
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
				
				.twoGroup{
					padding-bottom: 80rpx;
				}
				
				.other{
					position: absolute;
					padding: 20rpx 0;
					bottom: 20rpx;
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
