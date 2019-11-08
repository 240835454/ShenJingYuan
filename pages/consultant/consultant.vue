<template>
	<view class="page">
		<view class="box">
			<template v-for='(item,index) in chatList'>
				<view class="content" :key='index' @click='enterChat'>
					<image :src="item.img" mode="aspectFill" class='image'></image>
					<view class="info">
						<text class='name'>{{item.name}}</text>
						<text>{{item.text}}</text>
					</view>
					<view class="time">
						{{item.time}}
					</view> 
				</view> 
			</template> 
		</view>
	</view> 
</template>

<script>
	export default{
		data(){
			return{
				chatList: [
					{
						img: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1573189931852&di=41339866e56c8c3691d0a59d16cc22fe&imgtype=0&src=http%3A%2F%2Fimg13.360buyimg.com%2Fn1%2Fs350x449_jfs%2Ft20185%2F85%2F1836305557%2F53382%2Fb5d144e2%2F5b350779N27298e06.jpg%2521cc_350x449.jpg',
						name: '咨询师 01',
						text: '哈哈哈哈哈或或或或或或或或或或或或或或或或或',
						time: '10:16'
					},
					{
						img: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1573189931852&di=41339866e56c8c3691d0a59d16cc22fe&imgtype=0&src=http%3A%2F%2Fimg13.360buyimg.com%2Fn1%2Fs350x449_jfs%2Ft20185%2F85%2F1836305557%2F53382%2Fb5d144e2%2F5b350779N27298e06.jpg%2521cc_350x449.jpg',
						name: '咨询师 01',
						text: '哈哈哈哈哈或或或或或或或或或或或或或或或或或',
						time: '10:16'
					},					{
						img: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1573189931852&di=41339866e56c8c3691d0a59d16cc22fe&imgtype=0&src=http%3A%2F%2Fimg13.360buyimg.com%2Fn1%2Fs350x449_jfs%2Ft20185%2F85%2F1836305557%2F53382%2Fb5d144e2%2F5b350779N27298e06.jpg%2521cc_350x449.jpg',
						name: '咨询师 01',
						text: '哈哈哈哈哈或或或或或或或或或或或或或或或或或',
						time: '10:16'
					},					{
						img: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1573189931852&di=41339866e56c8c3691d0a59d16cc22fe&imgtype=0&src=http%3A%2F%2Fimg13.360buyimg.com%2Fn1%2Fs350x449_jfs%2Ft20185%2F85%2F1836305557%2F53382%2Fb5d144e2%2F5b350779N27298e06.jpg%2521cc_350x449.jpg',
						name: '咨询师 01',
						text: '哈哈哈哈哈或或或或或或或或或或或或或或或或或',
						time: '19/10/31'
					}
				]
			}
		},
		methods:{
			enterChat(){
				uni.navigateTo({
					url: 'community'
				}) 
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
		.content {
			display: flex;
			padding: 20rpx;
			margin-bottom: 20rpx;
			background-color: #fff;
			.image{
				flex: 0 0 120rpx;
				height: 120rpx;
			}
			.info{
				display: flex;
				flex-direction: column;
				justify-content: space-around;
				padding-left: 20rpx; 
				font-size: 28rpx;
				color: #cccccc;
				.name{
					font-size: 34rpx;
					color: #80899c;
				}
				text{
					display: block;
					width: 400rpx;
					overflow: hidden;
					text-overflow: ellipsis;
					display: -webkit-box;
					-webkit-line-clamp: 1;
					-webkit-box-orient: vertical;
				}
			}
			.time{
				width: 120rpx;
				padding-left: 10rpx;
				text-align: right;
				font-size: 28rpx;
				color: #80899c;
			}
		}
	}
</style>
