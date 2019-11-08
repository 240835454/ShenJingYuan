<template>
	<view class="page">
		<view class="footer">
			<textarea value="" placeholder="请输入您想咨询的问题..." class='textarea-box' auto-height="true" placeholder-class="phcolor" @linechange='lineChange' />
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				
			}
		},
		methods:{
			lineChange(e){
			}
		}
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
	}
	
	.footer{
		position: fixed;
		display: flex;
		align-items: center;
		width: 100%;
		line-height: 100rpx;
		padding: 20rpx;
		background-color: #fff;
		bottom: 0;
		.textarea-box{
			width: 500rpx;
			height: 50rpx;
			padding: 10rpx 0 0 20rpx;
			border: 2rpx solid #e0e4ee;
			line-height: 0;
		}
		.phcolor{
			font-size: 30rpx;
			color: #cccccc;
		}
	}
</style>
  