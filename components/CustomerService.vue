<template>
	<view class="cs_panel">
		<button class="cs_btn" @click="open">客服</button>
		<uni-popup ref="popup" class="cs_popup" type="center">
			<view class="cs_popup_content">
				<uni-icons type="closeempty" class="cs_close" @click="close"></uni-icons>
				<uni-icons type="headphones" size="60" color="#F89E1C" class="cs_header"></uni-icons>
				<view class="cs_store cs_store1">
					<uni-icons type="shop-filled" size="24"></uni-icons>
					<text>最强美容店</text>
				</view>
				<view class="cs_store cs_store2">
					<view class="cs_phone">
						<uni-icons type="phone" size="24"></uni-icons>
						<text>187388998</text>
					</view>
					<button type="primary" class="ring_up" :loading="ringUpLoading" @click="ringUp">拨打客服电话</button>
				</view>
				<view class="cs_store">
					<uni-icons type="paperplane" size="24"></uni-icons>
					<text>深圳市高新园帝国大厦23330号haodya深圳市高新园帝国大厦</text>
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
			background-color: transparent;
		}
		.cs_btn::after{
			display: none;
		}
		.cs_popup_content{
			border-radius: 10px;
			padding: 20px 30px;
			box-sizing: border-box;
			max-width: 90vw;
			background-color: #fff;
			color: #333;
			.cs_close{
				position: absolute;
				right: 10px;
				top: 10px;
				width: 15px;
				height: 15px;
			}
		
			.cs_header{
				margin: 10px auto 40px;
				display: block;
			}
			
			.cs_store{
				display: flex;
				align-items: center;
				justify-content: flex-start;
				border-top: 1px solid #DDD;
				padding: 10px 8px 10px 2px;
				:deep(.uni-icons){
					margin-right: 10px;
				}
				.cs_phone{
					display: flex;
					align-items: center;
				}
				.ring_up{
					background-color: #F89E1C;
				}
			}
		
			.cs_store1{
				border-top: none;
			}
			.cs_store2{
				justify-content: space-between;
			}
			
		
		}
		
	}
</style>