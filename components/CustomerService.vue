<template>
	<view class="cs_panel">
		<button type="primary" class="cs_btn" @click="open">客服</button>
		<uni-popup ref="popup" class="cs_popup" type="center">
			<view class="cs_popup_content">
				<uni-icons type="closeempty" class="cs_close" @click="close"></uni-icons>
				<uni-icons type="headphones" class="cs_header"></uni-icons>
				<view class="cs_store">
					<uni-icons type="shop-filled"></uni-icons>
					<text>最强美容店</text>
				</view>
				<view class="cs_store">
					<uni-icons type="phone"></uni-icons>
					<text>187388998</text>
					<button type="primary" class="ring_up" :loading="ringUpLoading" @click="ringUp">拨打客服电话</button>
				</view>
				<view class="cs_store">
					<uni-icons type="paperplane"></uni-icons>
					<text>深圳市高新园帝国大厦23330号haodya</text>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script setup>
	import { ref } from 'vue'
	
	const popup = ref(null)
	const ringUpLoading = ref(false)
	
	function open() {
		popup.value.open()
	}
	
	function close() {
		console.log('close popup')
		popup.value.close()
	}
	
	function ringUp() {
		ringUpLoading.value = true
		uni.makePhoneCall({
			phoneNumber: '114',
			fail: () => {
				uni.showToast({
					title: '拨打失败请重试',
					icon: 'error',
					duration: 2000
				});
			},
			complete: () => {
				ringUpLoading.value = false
			}
		})
		
	}
	
</script>

<style lang="scss" scoped>
	.cs_panel{
		.cs_btn{
			
		}
		.cs_popup_content{
			border-radius: 10px;
			padding: 20px;
			background-color: #fff;
			color: #333;
			font-size: 18px;
			.cs_close{
				position: absolute;
				right: 10px;
				top: 10px;
				width: 15px;
				height: 15px;
			}
		
			.cs_header{
				margin: 0 auto 40px;
				font-size: 60px;
				color: #F89E1C;
			}
			
			.cs_store{
				display: flex;
				align-items: center;
				justify-content: center;
				
				.ring_up{
					background-color: #F89E1C;
					
				}
			}
		
			.cs_store:not(:nth-child(1)){
				// border-top: none;
				border-top: 1px solid #DDD;
			}
			
		
		}
		
	}
</style>