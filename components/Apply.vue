<template>
	<view class="apply_panel">
		<button class="apply" @click="open">立即报名</button>
		<uni-popup ref="popup" class="apply_popup" type="center">
			<view class="apply_popup_content">
				<view class="tips">
					长按下面的二维码添加客服报名
				</view>
				<view class="img_panel">
					<image class="img" mode="aspectFit" :src="src"></image>
				</view>
				<button type="primary" class="sure" @click="close">关闭</button>
			</view>
		</uni-popup>
	</view>
</template>

<script setup>
	import { ref } from 'vue'
	
	const popup = ref(null)
	const src = ref('/static/uni-h5-hosting-qr.png')
	
	function open() {
		popup.value.open()
	}
	
	function close() {
		popup.value.close()
	}
</script>

<style lang="scss" scoped>
	.apply_panel{
		.apply{
			background-color: transparent;
		}
		.apply::after{
			display: none;
		}
		.apply_popup_content{
			border-radius: 10px;
			padding: 20px 30px;
			box-sizing: border-box;
			max-width: 90vw;
			background-color: #fff;
			color: #333;
		
			
			.tips{
				font-size: 16px;
				font-weight: bold;
				text-align: center;
			}
			.img_panel{
				margin: 18px auto;
				display: flex;
				align-items: center;
				justify-content: center;
			}
		}
		
	}
</style>