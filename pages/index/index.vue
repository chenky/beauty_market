<template>
	<view class="container">
		<view class="header_promotion">
			<image class="img" mode="aspectFill" :src="promotionSrc"></image>
		</view>
		<view class="activity">
			<image class="img" mode="aspectFill" :src="activitySrc"></image>
		</view>
		<view class="qa">
			<image class="img" mode="aspectFill" :src="qaSrc"></image>
		</view>
		<view class="store_explanation">
			<image class="img" mode="aspectFill" :src="professorSrc"></image>
			<image class="img" mode="aspectFill" :src="envSrc1"></image>
			<image class="img" mode="aspectFill" :src="envSrc2"></image>
		</view>
		<view class="music" @click="play">
			<uni-icons type="sound" size="20"></uni-icons>
		</view>
		<!-- <view class="generate_poster"></view> -->
		<view class="tabbar">
			<CustomerService></CustomerService>
			<button class="share" @click="share">分享</button>
			<Apply></Apply>
		</view>
		<view class="mask" v-show="isShareTip" @click="maskClick">
			<ShareArrowTip class="share_arrow_tip"></ShareArrowTip>
		</view>
	</view>
</template>

<script setup>
	import { ref } from 'vue'
	import CustomerService from '../../components/CustomerService.vue'
	import Apply from '../../components/Apply.vue'
	import ShareArrowTip from '../../components/ShareArrowTip.vue'
	
	const promotionSrc = ref('https://img.tusij.com/ips_templ_preview/2020-09-23/07/078ab89c-ed42-423f-8e68-d44531905fc2.jpg?auth_key=2330412046-0-0-ec55cc87ce626a58c4563a5036a20cf0&x-oss-process=image/resize,m_fixed,w_750/crop,x_0,y_0,w_750')
	const activitySrc = ref('https://imgs.design006.com/202205/Design006_AeEJHEPcra.jpg?x-oss-process=style/prev_w_750_h_auto')
	const qaSrc = ref('https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fsafe-img.xhscdn.com%2Fbw1%2F331f3b00-d5b3-43aa-a1c9-aedf8c83d615%3FimageView2%2F2%2Fw%2F1080%2Fformat%2Fjpg&refer=http%3A%2F%2Fsafe-img.xhscdn.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1700556949&t=9c304affd6b829233a3d38fa5171053d')
	const professorSrc = ref('https://imgpp.ztupic.com/u/3k0AX0FwjN/1627434663818_00706a22.jpg?x-oss-process=image/resize,w_750/quality,q_85/watermark,image_d2F0ZXIucG5n,type_ZmFuZ3poZW5naGVpdGk')
	const envSrc1 = ref('https://img1.baidu.com/it/u=2170287429,1536144529&fm=253&fmt=auto&app=138&f=JPEG?w=750&h=750')
	const envSrc2 = ref('https://pic1.zhimg.com/v2-845d4b5824fbf2bcf86e4ab7c60a250e_1440w.jpg?source=172ae18b')
	
	const isShareTip = ref(false)
	
	const innerAudioContext = uni.createInnerAudioContext();
	innerAudioContext.autoplay = true;
	innerAudioContext.loop = true;
	innerAudioContext.play()
	innerAudioContext.src = 'https://bjetxgzv.cdn.bspapp.com/VKCEYUGU-hello-uniapp/2cc220e0-c27a-11ea-9dfb-6da8e309e0d8.mp3';
	function play() {
		innerAudioContext[innerAudioContext.paused?'play':'pause']()
	}
	
	function share() {
		isShareTip.value = true
	}
	function maskClick() {
		isShareTip.value = false
	}

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
		// padding: 20px;
		font-size: 14px;
		line-height: 24px;
		padding-bottom: 40px; 
		uni-image{
			width: 100%;
			height: 700px;
			display: block;
		}
		.music{
			position: fixed;
			right: 5px;
			top: 20px;
			z-index: 5;
			width: 30px;
			height: 30px;
			border-radius: 50%;
			display: flex;
			align-items: center;
			justify-content: center;
			background-color: #dddddd;
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
			padding-bottom: constant(safe-area-inset-bottom);
			padding-bottom: env(safe-area-inset-bottom); 
			z-index: 90;
			.share{
				// background-color: #F89E1C;
				border-left: 1px solid #DDD;
				border-right: 1px solid #DDD;
			}
		}
		.mask{
			position: fixed;
			top: 0;
			left: 0;
			right: 0;
			bottom: 0;
			background-color: #dddddde0;
			padding-bottom: 40px;
			z-index: 20;
			.share_arrow_tip{
				display: block;
				position: absolute;
				width: 100px;
				top: 0;
				right: 20px;
				fill: #F89E1C;
			}
		}
	}
</style>
