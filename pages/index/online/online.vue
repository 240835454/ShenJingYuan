<template>
	<view class="page">
		<view class="content">
			<template v-for="(item,index) in questionnaireList">
				<view class='guide' :key='index' @click='enterDetail'>
					<image :src="item.img" mode=""></image>
					<view class="message">
						<text class='title'>{{item.title}}</text>
						<view class="info">
							<view class='date'>
								<image src="../../../static/icon_time.png" mode="widthFix"></image>
								<text>{{item.date}}</text>
							</view>
						</view>
					</view>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				questionnaireList: [{
						img: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1487361593,1220453903&fm=26&gp=0.jpg',
						title: '健康调查简表，SF-36',
						date: '2019.10.30 - 2019.11.25'
					},
					{
						img: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1487361593,1220453903&fm=26&gp=0.jpg',
						title: '健康调查简表，SF-36',
						date: '2019.10.30 - 2019.11.25'
					}, {
						img: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1487361593,1220453903&fm=26&gp=0.jpg',
						title: '健康调查简表，SF-36',
						date: '2019.10.30 - 2019.11.25'
					}
				]
			}
		},
		methods: {
			enterDetail() {
				uni.navigateTo({
					url: 'evaluate'
				})
			}
		}
	}
</script>

<style lang="less">
	.content {
		padding: 20rpx 20rpx 120rpx 20rpx;
		.guide {
			margin-bottom: 20rpx;
			image {
				flex: 0 0 160rpx;
				height: 120rpx;
			}
		}
	}
</style>
