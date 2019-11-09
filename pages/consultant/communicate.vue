<template>
	<view class="page">
		<view class="chat-box" @click='closeOther' id="x_chat">
			<template v-for='(item,index) in chatList'>
				<view class='chat-item' :key='index' v-if='item.user === 1'>
					<image :src="item.avatar" mode="" class='avatar'></image>
					<text class='text'>{{item.text}}</text>
				</view>
				<view class='chat-item-reverse' :key='index' v-if='item.user === 2'>
					<text class='text'>{{item.text}}</text>
					<image :src="item.avatar" mode="" class='avatar'></image>
				</view>
			</template>
		</view>
		<view class="footer">
			<textarea v-model="message" placeholder="请输入您想咨询的问题..." class='textarea-box' auto-height="true" placeholder-class="phcolor"
			 @linechange='lineChange' @confirm='sendMsg' fixed="true" />
			<image src="../../static/icon_consulting_expression.png" mode="" class='icon' @click='showEmojiList'></image>
				<image src="../../static/icon_consulting_more.png" mode="" class='icon'></image>
			</view>
			<view class="emojiList" v-show='showEmoji' :style="{'bottom':chatBoxHeight}">
				<template v-for='(item,index) in emojiList'>
					<text :key='index' @click="chooseEmoji(item)">{{item}}</text>
				</template>
			</view>
	</view>
</template>

<script>
	import emoji from '@/public/js/emoji.js';
	export default{
		data(){
			return{
				showEmoji: false,
				message: '',
				chatBoxHeight: 0,
				chatList:[
					{
						user: 1,
						avatar: "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1004696383,1396271483&fm=11&gp=0.jpg",
						text: "早上好，有什么可以帮到您。"
					},
					{
						user: 2,
						avatar: "http://img3.imgtn.bdimg.com/it/u=1928846916,3022680481&fm=26&gp=0.jpg",
						text: "我想请问一下，我这个月的漏尿次数少了很多，正常吗？"
					},					{
						user: 1,
						avatar: "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1004696383,1396271483&fm=11&gp=0.jpg",
						text: "早上好，有什么可以帮到您。"
					},
					{
						user: 2,
						avatar: "http://img3.imgtn.bdimg.com/it/u=1928846916,3022680481&fm=26&gp=0.jpg",
						text: "我想请问一下，我这个月的漏尿次数少了很多，正常吗？"
					},					{
						user: 1,
						avatar: "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1004696383,1396271483&fm=11&gp=0.jpg",
						text: "早上好，有什么可以帮到您。"
					},
					{
						user: 2,
						avatar: "http://img3.imgtn.bdimg.com/it/u=1928846916,3022680481&fm=26&gp=0.jpg",
						text: "我想请问一下，我这个月的漏尿次数少了很多，正常吗？"
					},					{
						user: 1,
						avatar: "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1004696383,1396271483&fm=11&gp=0.jpg",
						text: "早上好，有什么可以帮到您。"
					},
					{
						user: 2,
						avatar: "http://img3.imgtn.bdimg.com/it/u=1928846916,3022680481&fm=26&gp=0.jpg",
						text: "我想请问一下，我这个月的漏尿次数少了很多，正常吗？"
					},					{
						user: 1,
						avatar: "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1004696383,1396271483&fm=11&gp=0.jpg",
						text: "早上好，有什么可以帮到您。"
					},
					{
						user: 2,
						avatar: "http://img3.imgtn.bdimg.com/it/u=1928846916,3022680481&fm=26&gp=0.jpg",
						text: "我想请问一下，我这个月的漏尿次数少了很多，正常吗？"
					}
				]
			}
		},
		onReady(){
			this.sendMsg();
		},
		computed:{
			emojiList(){
				return emoji;
			}
		},
		methods:{
			lineChange(e){ 
				this.chatBoxHeight = e.detail.heightRpx + 40 + 'rpx';  
			},
			showEmojiList(){
				this.showEmoji = !this.showEmoji;
			},
			chooseEmoji(e){
				this.message += e;
			},
			closeOther(){
				this.showEmoji = false;
			},
			sendMsg(){
				if(this.message != ''){
					this.chatList.push({
						user:2,
						avatar: "http://img3.imgtn.bdimg.com/it/u=1928846916,3022680481&fm=26&gp=0.jpg",
						text: this.message
					})
					this.message = ''; 
					this.showEmoji = false;
					//回到底部
					uni.createSelectorQuery().select('#x_chat').boundingClientRect(function(rect){
						console.log(rect);
						uni.pageScrollTo({
							scrollTop: rect.height,
							duration: 100
						})
					}).exec(); 
				}
			}
		}  
	}
</script> 

<style lang="less">
	page {
		width: 100%;
		height: 100%;
		background-color: #f9fafd;
	}
	
	.chat-box{
		overflow-y: hidden;
		padding-bottom: 150rpx;
		.chat-item{
			padding-top:40rpx;
			.avatar{
				width: 100rpx;
				height: 100rpx;
				padding:0 20rpx;
				vertical-align: top;
			}
			.text{
				display: inline-block;
				width: 450rpx;
				padding: 30rpx;
				font-size: 34rpx;
				color: #80899c;
				background-color: #fff;
				box-shadow: 0px 4px 20px 0px 
						rgba(166, 181, 213, 0.1);
			}
		}
		
		.chat-item-reverse{
			display: flex;
			justify-content: flex-end;
			.chat-item;
			.text{
				color: #fff;
				background-color: #a6b5d5;
			}
		}
	}
	
		.footer{
			position: fixed;
			display: flex;
			align-items: center;
			width: 100%;
			padding: 20rpx;
			background-color: #fff;
			bottom: 0;
			z-index: 10;
			.textarea-box{
				width: 500rpx;
				// height: 50rpx;
				padding: 10rpx 0 0 20rpx;
				border: 2rpx solid #e0e4ee;
				line-height: 0;
				font-size: 30rpx;
			}
			.phcolor{
				position: fixed;
				bottom: 0;
				font-size: 30rpx;
				color: #cccccc;
			}
			.icon{
				padding-left: 30rpx;
				width: 50rpx;
				height: 50rpx;
			}
		}
		
		.emojiList{
			position:fixed; 
			bottom: 90rpx;
			padding: 20rpx;
			background-color: #fff;
			font-size: 50rpx;
			text{
				display: inline-block;
				padding: 0 10rpx;
			}
		}
	
</style>
