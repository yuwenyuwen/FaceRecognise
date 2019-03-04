<template>
	<view class="container">
		<view class="item">
			<view class="item-label">
				课程名称：
			</view>
			<view class="item-value">
				<input class="item-input" v-model="courseName"></input>
			</view>
		</view>
		<view class="item">
			<view class="item-label">
				课程时间：
			</view>
			<view class="item-value">
				<input class="item-input" v-model="courseTime"></input>
			</view>
			<!--<view class="uni-list">
				 <view class="uni-list-cell">
					<view class="uni-list-cell-left">
						当前选择
					</view>
					<view class="uni-list-cell-db">
						<picker mode="time" :value="time" start="09:01" end="21:01" @change="bindTimeChange">
							<view class="uni-input">{{time}}</view>
						</picker>
					</view>
				</view> 
			</view>-->
			<!-- <view class="item-value">
				<picker-view v-if="visible"  :value="value" @change="bindChange">
					<picker-view-column>
						<view class="item" v-for="(item,index) in years" :key="index">{{item}}年</view>
					</picker-view-column>
					<picker-view-column>
						<view class="item" v-for="(item,index) in months" :key="index">{{item}}月</view>
					</picker-view-column>
					<picker-view-column>
						<view class="item" v-for="(item,index) in days" :key="index">{{item}}日</view>
					</picker-view-column>
				</picker-view>
			</view> -->
		</view>
		<view class="item">
			<view class="item-label">
				课程人数：
			</view>
			<view class="item-value">
				<input class="item-input" v-model="courseNum"></input>
			</view>
		</view>
		<view class="item">
			<view class="item-label">
				课程简介：
			</view>
			<view class="item-value">
				<input class="item-input" v-model="courseDes"></input>
			</view>
		</view>
		<button @click="commit">提交</button>
	</view>
</template>

<script>
	import axios from 'axios'
	export default {
		data() {
			const date = new Date()
			const years = []
			const year = date.getFullYear()
			const months = []
			const month = date.getMonth() + 1
			const days = []
			const day = date.getDate()
			for (let i = 1990; i <= date.getFullYear(); i++) {
				years.push(i)
			}
			for (let i = 1; i <= 12; i++) {
				months.push(i)
			}
			for (let i = 1; i <= 31; i++) {
				days.push(i)
			}
			return {
				courseName:"",
				courseTime:"",
				courseNum:"",
				courseDes:"",
				title: 'picker-view',
				time:"",
				years,
				year,
				months,
				month,
				days,
				day,
				value: [9999, month - 1, day - 1],
				visible: true,
				indicatorStyle: `height: 100px;`
			};
		},
		methods:{
			click(){
				uni.showToast({
					title: '标题',
					content:"hello",
					duration: 2000
				});
			},
			bindChange: function (e) {
				const val = e.detail.value
				this.year = this.years[val[0]]
				this.month = this.months[val[1]]
				this.day = this.days[val[2]]
			},
			bindTimeChange(){
				
			},
			commit(){
				uni.request({
					url: 'https://www.example.com/request', //仅为示例，并非真实接口地址。
					data: {
						text: 'uni.request'
					},
					header: {
						'custom-header': 'hello' //自定义请求头信息
					},
					success: (res) => {
						console.log(res.data);
						this.text = 'request success';
					}
				});
			}
		},
		watch:{
			courseName(val){
				console.log(val)
			}
		}
	}
</script>

<style>
	.container{
		flex-direction: column;
		padding: 10px;
	}
	.item{
		display: flex;
		flex-direction: column;
		padding:15px;
		height:30px;
	}
	.item-label{
		font-size: 14px;
	}
	.item-value{
		flex:1;
	}
	.item-input{
		flex:1;
		border:#eee 1px solid
	}
	button{
		margin:20px 0;
		background: #09BB07;
		color:white
	}
</style>
