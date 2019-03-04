/*我的课程页面*/
<template>
	<view class="center">
		<view class="logo" @click="goLogin" :hover-class="!login ? 'logo-hover' : ''">
			<image class="logo-img" :src="login ? uerInfo.avatarUrl :avatarUrl"></image>
			<view class="logo-title">
				<text class="uer-name">{{uerInfo.name}}</text>
			</view>
		</view>
		<view class="container">
			<template v-for="(i,index) in uerInfo.detail">
				<view class="item">
					<view class="item-title">
						<text class="title-key">课程名称</text>
						<text class="title-value">{{i.key}}</text>
					</view>
					<view class="content">
						<view class="item-content">
							<view class="content-key">课程内容:</view>
							<view class="content-value">{{i.content}}</view>
						</view>
						<view class="item-content">
							<view class="content-key">课程时间:</view>
							<view class="content-value">{{i.time}}</view>
						</view>
						<view class="item-content">
							<view class="content-key">参课人数:</view>
							<view class="content-value">{{i.num}}</view>
						</view>
					</view>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
	import {uniCard} from '@dcloudio/uni-ui'
	export default {
		components: {uniCard},
		data() {
			return {
				login: false,
				avatarUrl: "../../static/img/my/logo.png",
				uerInfo: {
					name:"刘老师",
					detail:[
						{
							key:'计算机组成原理',
							title:'课程名称',
							content:'讲解计算机组成原理相关知识讲',
							time:"20190301",
							num:"20/30",
						},{
							key:'操作系统',
							title:'课程名称',
							content:'操作系统',
							time:"20190302",
							num:"18/20",
						}
					],
				},
			}
		},
		methods: {
			goLogin() {
				if (!this.login) {
					uni.navigateTo({url:'login'})
				}
			},
		}
	}
</script>

<style>
	@font-face {
		font-family: texticons;
		font-weight: normal;
		font-style: normal;
		src: url('https://at.alicdn.com/t/font_984210_5cs13ndgqsn.ttf') format('truetype');
	}

	page,
	view {
		display: flex;
	}

	page {
		background-color: #f8f8f8;
	}

	.center {
		flex-direction: column;
	}
	.container{
		flex-direction: column;
	}
	.logo {
		width: 750upx;
		height: 240upx;
		padding: 20upx;
		box-sizing: border-box;
		background-color: #4cd964;
		flex-direction: row;
		align-items: center;
	}

	.logo-hover {
		opacity: 0.8;
	}

	.logo-img {
		width: 150upx;
		height: 150upx;
		border-radius: 150upx;
	}

	.logo-title {
		height: 150upx;
		flex: 1;
		align-items: center;
		justify-content: space-between;
		flex-direction: row;
		margin-left: 20upx;
	}
	.item{
		margin:10px;
		flex-direction: column;
		border:#eee 1px solid;
		background:white;
	}
	.item-title{
		width:100%;
		display:flex;
		border-left: #09BB07 5px solid;
		border-bottom: #eee 1px solid;
		padding:10px;
		box-sizing: border-box;
	}
	.title-key{
		flex:1
	}
	.title-value{
		flex:1;
		text-align: right;
	}
	.content{
		flex-direction: column;
	}
	.item-content{
		padding:5px 20px;
		display: flex;
		flex-flow: row;
	}
	.content-key{
		width:60px;
		margin-right:10px
	}
	.content-value{
		text-align: left;
	}
</style>