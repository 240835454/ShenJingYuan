<template>
	<view class="page">
		<view class="content">
			<view class="box">
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
								<label :key='index' class="radio"  @click='selectBladder(index)'>
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
				gender: ['男性','女性'],
				isInfect: ['有','无'],
				bladder: ['正常或高','低'],
				course: ['<=5年','>5年'],
				incontinence: ['有','无'],
				genderIndex: -1,
				isInfectIndex: -1,
				bladderIndex: -1,
				courseIndex: -1,
				incontinenceIndex: -1,
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
		}
	}
</script>

<style lang="less">
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
			}
			
			.footer {
				padding: 200rpx 0 60rpx;
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
</style>
