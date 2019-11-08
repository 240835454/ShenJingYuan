<template>
	<view class="page">
		<view class="content">
			<text class='title'>{{title}}</text>
			<view class="info">
				<view class='date'>
					<image src="../../../static/icon_time.png" mode="widthFix"></image>
					<text>{{date}}</text>
				</view>
				<view class='visit'>
					<image src="../../../static/icon_browse.png" mode="widthFix"></image>
					<text>{{visiter}}</text>
				</view>
			</view>
			<view class="picture">
				<image src="../../../static/图层2.png" mode=""></image>
			</view>
			<view class="">
				<text>
					避免高GI的食物GI =（Glycemic Index）“血糖生成指数”——是反映食物引起人体血糖升高程度的指标，当你食用高GI的食物后，短时间内血糖值上升程度高，这时候身体就会分泌胰岛素将吃进体内的热量转化为糖原、脂肪存储起来。而低GI的食物比较容易产生饱腹感，同时引起较低的胰岛素水平。打个比喻，血糖上升还比天上掉钱，细胞好比是你。血糖上升慢，好比天上掉钱是一张一张慢慢掉，于是你就能很高效的捡到所有的钱。细胞很好的吸收这些营养物质。血糖上升快，好比天上一下子掉下一百万的现金，你一把抓过去只能抓到几张，效果很差。剩下的就变成了脂肪储存起来。我们日常吃的精致碳水比如蛋糕、饼干、含糖量高的食物都是高GI，长期下去也容易导致胰岛素的抵抗，于是你身体为了降低血糖值就必须分泌更多的胰岛素，这样带来的后果就是肥胖，而肥胖就又会带来胰岛素抵抗，陷入一个死循环。低GI食物就有粗粮、豆类、豆腐、还有全麦或高纤食品等等。这里有一份食物的GI值表，可以大概参考。
				</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: "如何在两个月内瘦40斤？",
				date: "2019.10.30  20:43",
				visiter: "1855"
			}
		}
	}
</script>

<style lang="less">
	page {
		height: 100%;
		background-color: #f9fafd;
	}

	.page {
		padding: 40rpx 60rpx;

		.content {
			.title {
				font-size: 38rpx;
				color: #333333;
			}

			.info {
				display: flex;
				justify-content: space-between;
				width: 405rpx;
				font-size: 24rpx;
				color: #cccccc;
				padding-top: 24rpx;
				.date {
					display: flex;
					align-items: center;

					image {
						flex: 0 0 26rpx;
						width: 26rpx;
						heihgt: 26rpx;
						padding-right: 12rpx;
					}
				}

				.visit {
					display: flex;
					align-items: center;

					image {
						flex: 1 1 30rpx;
						width: 30rpx;
						height: 25rpx;
						padding-right: 12rpx;
					}
				}
			}
			.picture{
				margin-top: 40rpx;
				image{
					width: 100%;
					height: 470rpx;
				}
			}
		}
	}
</style>
