<template>
    <view>
        <!-- <camera device-position="back" flash="off" @error="error" style="width: 100%; height: 300px;"></camera> -->
		<div class="img-spec-div">
			<camera  class="img-spec" device-position="back" flash="off" binderror="error" style="width: 100%; height: 300px;" v-if="control.showCamera"></camera>
			<image  class="img-spec" mode="widthFix" :src="src" v-if="!control.showCamera" style="width: 100%; height: 300px;"></image>
		</div>
        <button class="take-photo-btn" type="primary" @click="takePhoto" v-if="control.showCamera">拍照</button>
		<div class="button-group" v-if="!control.showCamera">
			<button class="spec-button" @click="recognise(1)">算法一</button>
			<button class="spec-button" @click="recognise(2)">算法二</button>
			<button class="spec-button" @click="recognise(3)">算法三</button>
		</div>
		<div class="result-spec">
			<span>{{result}}</span>
		</div>
    </view>
</template>
<script>
export default {
    data() {
        return {
            src:"",
			control:{
				showCamera:true
			},
			result:"welcome...."
        }
    },
    methods: {
		takePhoto(){
			const ctx = wx.createCameraContext()
			ctx.takePhoto({
			  quality: 'high',
			  success: (res) => {
				  this.control.showCamera = false
				  this.src = res.tempImagePath
			  }
			})
		},
		recognise(flag){
			switch(flag){
				case 1:
					//todo
					this.result="result1"
					break;
				case 2:
					//todo
					this.result="result2"
					break;
				case 3:
					//todo
					this.result="result3"
					break;
			}
		}
    },
}
</script>
<style>
	.button-group{
		text-align: center;
	}
	.spec-button{
		display: inline-block;
		width:30%;
		border-radius: 5px;
		margin:20px 2px;
	}
	.img-spec-div{
		text-align: center;
		padding: 20px;
	}
	.img-spec{
		border-radius: 50%;
	}
	.take-photo-btn{
		margin:20px 20%;
	}
	.result-spec{
		text-align: center;
		font-size: 20px;
	}
</style>