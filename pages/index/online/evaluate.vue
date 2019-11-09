<template>
	<view class="page">
		<view class="box">
			<view class="content">
				<view class="title">
					<text>神经源性膀胱上尿路损害预测问卷表简表</text>
				</view>
			</view>
			<view v-show='active'>
				<view class="item">
					<text class='name'>(多选)您漏尿的次数？</text>
					<view class="checkBox'">
						<checkbox-group class=''>
							<template v-for="(item,index) in preventList">
								<label class='checkBox-item' :key='index' @click='preventIndex(index)'>
									<checkbox value="cb" :checked="false" color="#FFCC33" style="transform:scale(0.7)" /><text :class="item.active ? 'isChoose' : ''">{{item.text}}</text>
								</label>
							</template>
						</checkbox-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>(单选) 我们想知道您认为自己的漏尿量是多少？在通常情况下，您的漏尿量是多少(不管您是否使用了防护用品）？</text>
					<view class="radio">
						<radio-group class='radio-group'>
							<template v-for="(item,index) in cleanList">
								<label class="radio-item" :key='index' @click='selectRadio(index)'>
									<radio :value="value" color='#fff' /><text :class="cleanIndex == index ? 'isChoose' : ''">{{item}}</text>
								</label>
							</template>
						</radio-group>
					</view>
				</view>
				<view class="footer">
					<text class='button' @click='nextPage'>
						下一页
					</text>
				</view>
			</view>
			<view v-show='!active'>
				<view class="item">
					<text class='name'>(单选)您漏尿的次数？</text>
					<view class="radio">
						<radio-group class='radio-group'>
							<template v-for="(item,index) in preventList2">
								<label class="radio-item" :key='index' @click='selectRadio(index)'>
									<radio :value="value" color='#fff' /><text :class="cleanIndex == index ? 'isChoose' : ''">{{item.text}}</text>
								</label>
							</template>
						</radio-group>
					</view>
				</view>
				<view class="item">
					<text class='name'>总体上看，漏尿对您日常生活的影响程度如何？(0:表示没有影响; 10:表示很大影响）</text>
					<input type="text" value="" class='input-box' placeholder-class="phcolor" placeholder="请输入0~10分" maxlength="5" />
					<text class='name'>漏尿情况</text>
					<textarea type="text" value="" class='textarea-box' placeholder-class="phcolor" placeholder="请输入漏尿情况" />
					</view>
				<view class="footer">
					<text class='button' @click='openModel'>
						确认提交
					</text>
				</view>
				<view class="mask" v-show="isHide">
				</view>
				<view class="model" v-show="isHide">
					<text>您的在线评测分数为</text>
					<image src="../../../static/illustration_test_scores.png" mode="" class='image'></image>
					<text class='score'>{{score}}</text>
					<view class="desc">
						<text>{{mild}}</text>
						<text>{{moderate}}</text>
						<text>{{serious}}</text>
					</view>
					<view class="">
						<text class='button' @click='confirm'>确定</text>
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
				TabList: [
					'清洁间歇导尿推荐方案',
					'预防泌尿系感染'
				],
				activeIndex: 0,
				active: true,
				cleanList: [
					'不漏尿',
					'少量漏尿',
					'中等漏尿',
					'大量漏尿',
				],
				preventList: [{
						text: '从来不漏尿',
						active: false
					},
					{
						text: '一星期大约漏尿1次或经常不到1次',
						active: false
					},
					{
						text: '一星期漏尿2次或3次',
						active: false
					},
					{
						text: '每天大约漏尿1次',
						active: false
					},
					{
						text: '一天漏尿数次',
						active: false
					},
					{
						text: '一直漏尿',
						active: false
					}
				],
				preventList2: [{
						text: '从来不漏尿',
						active: false
					},
					{
						text: '一星期大约漏尿1次或经常不到1次',
						active: false
					},
					{
						text: '一星期漏尿2次或3次',
						active: false
					},
					{
						text: '每天大约漏尿1次',
						active: false 
					},
				],
				waterPlanState: true,
				urinatePlanState: false,
				cleanIndex: -1,
				isHide: false,
				mild: '轻度：总分≤7分；',
				moderate : '中度：7分<总分<14分；',
				serious: '重度：14分≤总分≤21分。',
				score: '9'
			}
		},
		methods: {
			changeTab(e) {
				this.activeIndex = e;
			},
			radioChange(e) {
				console.log(e);
			},
			waterPlan(e) {
				this.waterPlanState = !this.waterPlanState;
			},
			urinatePlan(e) {
				this.urinatePlanState = !this.urinatePlanState;
			},
			selectRadio(e) {
				this.cleanIndex = e;
			},
			preventIndex(e) {
				this.preventList[e].active = !this.preventList[e].active;
			},
			nextPage() {
				this.active = !this.active;
			}, 
			openModel(){ 
				this.isHide = !this.isHide;
			},
			confirm(){
				this.isHide = !this.isHide;
			}
		},
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
	}

	.box {
		padding: 20rpx;

		.content {
			background-color: #fff;
			text-align: center;

			.title {
				padding: 50rpx 120rpx;
				font-size: 34rpx;
				color: #333333;
				text-align: align;

				text {
					display: block;
					text-align: align;
				} 
			}
		}

		.item {
			color: #80899c;
			background-color: #fff;
			padding: 0 15rpx;
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
			
			.input-box{
				height: 70rpx;
				padding-left:20rpx;
				margin: 20rpx 0;
				border: 2rpx solid #e0e4ee;
				font-size: 30rpx;
			}
			
			.textarea-box{
				width: 100%;
				height: 220rpx;
				padding: 20rpx;
				margin-top: 20rpx;
				border: 2rpx solid #e0e4ee;
				box-sizing: border-box;
				font-size: 30rpx;
			}
			
			.phcolor{
				font-size: 30rpx;
				color: #cccccc;
			}

			.checkBox {
				display: flex;
				padding: 20rpx;
				font-size: 30rpx;
				color: #a6b5d5;

				.checkBox-item {
					display: flex;
					align-items: center;
					padding: 10rpx 0;
				}

				text {
					display: block;
					padding-left: 20rpx;
				}
			}

			.radio {
				display: flex;
				padding: 30rpx;
				font-size: 30rpx;
				color: #a6b5d5;

				.radio-item {
					display: flex;
					align-items: center;
					padding-bottom: 30rpx;
				}

				text {
					display: block;
					padding-left: 20rpx;
				}
			}

			.isChoose {
				color: #80899c;
			}
		}

		.footer {
			padding: 40rpx 0 60rpx 0;
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
		
		.mask{
			position: fixed;
			top: 0;
			bottom: 0;
			left: 0;
			right: 0;
			background-color: #000;
			opacity: 0.3;
			z-index:5;
		}
		
		.model{
			position: absolute;
			top: 200rpx;
			left: 50%;
			transform: translateX(-50%);
			width: 600rpx;
			padding:40rpx 80rpx 80rpx;
			text-align: center;
			font-size: 34rpx;
			background-color: #fff;
			z-index: 10;
			box-sizing: border-box;
			text{
				display: block;
			}
			.image{
				margin: 50rpx 0;
				width: 450rpx;
				height:280rpx;
			}
			.desc{
				padding:0 40rpx 40rpx;
				text-align: left;
				font-size: 28rpx;
				letter-spacing: 1px;
				color: #80899c;
			}
			.score{
				position: absolute;
				top: 35%;
				left: 50%;
				transform: translate(-50%,-35%);
				font-size: 120rpx;
				color: #a69eff;
				&::after{
					content: '分';
					padding-left: 20rpx;
					font-size: 63rpx;
				}
			}
			.button{
				padding: 20rpx 170rpx;
				color: #fff;
					background-image: linear-gradient(0deg, 
						#a69eff 0%, 
						#ccc7ff 100%), 
					linear-gradient(
						#ffffff, 
						#ffffff);
					background-blend-mode: normal, 
						normal;
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

	checkbox {
		border-radius: 50%;
		width: 60rpx;
		height: 60rpx;
	}

	checkbox .wx-checkbox-input {
		border-radius: 50%;
		width: 60rpx;
		height: 60rpx;
	}

	checkbox .wx-checkbox-input.wx-checkbox-input-checked {
		border: 1rpx solid #a6b5d5;
	}

	checkbox .wx-checkbox-input.wx-checkbox-input-checked::before {
		content: "";
		width: 40rpx;
		height: 40rpx;
		background-color: #a6b5d5;
		border: 1rpx solid #d2ddf5;
		;
		border-radius: 50%;
		text-align: center;
	}
</style>
