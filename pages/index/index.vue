<template>
	<view class="content">
		<view class="text-area">
			<text class="title">{{title}}</text>
			<button @click='request'>测试</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
			uni.setNavigationBarTitle({
				title: '哈哈'
			})
		},
		methods: {
			request(){
				wx.request({
					url: 'http://192.168.1.199:8359/API/AreaInfo/GetAreaInfo?ParentId=0',
					success: res=>{
						console.log(res);
					}
				})
			},
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
