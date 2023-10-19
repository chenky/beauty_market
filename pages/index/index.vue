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
			<button type="primary">转发好友</button>
			<button type="primary">立即报名</button>
		</view>
	</view>
</template>

<script setup>
	import { ref } from 'vue'
	import CustomerService from '../../components/CustomerService.vue'
	
	const href = ref('https://www.baidu.com')
</script>

<style lang="scss" scoped>
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
		.intro{
			color: red;
		}
	}
</style>
