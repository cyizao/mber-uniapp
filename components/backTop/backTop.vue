<template>
	<view class="acea-row row-center-wrapper back-top" :style="{ top: top + 'px'}" @click="handleBackTop">
		<uni-icons type="top" size="25"></uni-icons>
	</view>
</template>

<script>
	export default {
		name:"backTop",
		data() {
			return {
				top: 510,
				disable: false // 禁止点击
			};
		},
		props: {
			isShowTop: {
				type: Boolean,
				default: false
			}
		},
		mounted() {
			// #ifdef H5
			this.top = parseFloat(window.innerHeight) - 135
			// #endif
		},
		methods: {
			handleBackTop() {
				if (this.disable) return
				this.$emit('backTop', 'top')
				this.disable = true
				// let timer = null
				// if (timer) {
				// 	clearTimeout(timer)
				// }
				// timer = setTimeout(() => {
				// 	this.disable = false
				// }, 300)
			}
		}
	}
</script>

<style lang="scss">
	.back-top {
		width: 96rpx;
		height: 96rpx;
		background: rgba(255, 255, 255, 0.8);
		box-shadow: 0 3rpx 16rpx rgba(0, 0, 0, 0.08);
		backdrop-filter: blur(10px);
		border-radius: 50%;
		font-size: 16rpx;
		color: #666;
		position: fixed;
		right: 15rpx;
		z-index: 9;
	}
</style>
