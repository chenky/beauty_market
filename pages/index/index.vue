<template>
	<view class="container">
		<view class="header_promotion"></view>
		<view class="activity"></view>
		<view class="activity_intro"></view>
		<view class="qa"></view>
		<view class="store_explanation"></view>
		<view class="music"></view>
		<view class="generate_poster"></view>
		<view class="tabbar">
			<CustomerService></CustomerService>
			<button class="share" open-type="share">转发好友</button>
			<Apply></Apply>
		</view>
	</view>
</template>

<script setup>
	import { ref } from 'vue'
	import CustomerService from '../../components/CustomerService.vue'
	import Apply from '../../components/Apply.vue'
	
	const href = ref('https://www.baidu.com')
</script>

<style lang="scss">
	.container {
		.tabbar{
			.cs_panel,.share,.apply_panel{
				flex:1;
			}
			.cs_btn,.share,.apply{
				border: none;
				border-radius: 0;
				background-color: transparent;
			}
			uni-button::after{
				display: none;
			}
		}
	}
</style>
<style lang="scss" scoped>
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
		.intro{
			color: red;
		}
		.tabbar{
			background-color: #fff;
			position: fixed;
			left: 0;
			bottom: 0;
			right: 0;
			display: flex;
			align-items: center;
			justify-content: space-evenly;
			padding: 10px 0;
			z-index: 90;
			.share{
				// background-color: #F89E1C;
				border-left: 1px solid #DDD;
				border-right: 1px solid #DDD;
			}
		}
	}
</style>
