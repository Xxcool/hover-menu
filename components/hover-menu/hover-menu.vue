<template>
	<view>
		<!-- 遮罩 -->
		<view class="mask" v-if="show" @tap="show = false" @touchmove.stop.prevent></view>
		<!-- 按钮 -->
		<view class="major-box" :class="{show: show}">
			<view class="click-btn" v-if="!show" @tap="show = !show" draggable="true" @touchstart="touchstart"
			 @touchmove.stop.prevent="touchmove">
				<view>&lt;&nbsp;快捷导航</view> </view> <view class="nav-box" v-if="show">
						<view class="nav-btn" v-for="(btn, index) in btnList" :key="index" @tap="clickBtn(btn.type)">
							<view class="nav-icon">
								<image class="icon" :src="btn.icon"></image>
							</view>
							<view class="nav-text">{{btn.text}}</view>
						</view>
				</view>
			</view>
		</view>
</template>

<script>
	export default {
		props: {
			dataId: {
				type: String,
				default: '',
			}
		},
		data() {
			return {
				show: false, // 是否显示
				deviationTop: 0, // 偏移量
				windowHeight: uni.getSystemInfoSync().windowHeight, // 视图高度 
				btnList: [ // 所有按钮 
					{
						text: '首页',
						icon: '../../static/icon-home.png',
						type: 1
					},
					{
						text: '列表',
						icon: '../../static/icon-add.png',
						type: 2
					},
					{
						text: '列表详情',
						icon: '../../static/icon-visit.png',
						type: 3
					},
				]
			};
		},
		methods: {
			// 点击按钮 
			clickBtn: function(type) {
				this.show = false
				if (type == 1) {
					uni.navigateTo({
						url: '/pages/customer/list'
					});
				}
				if (type == 2) {
					uni.navigateTo({
						url: '/pages/customer/new'
					});
				}
				if (type == 3) {
					uni.navigateTo({
						url: `/pages/customer/visit-record/new?id=${this.dataId}`
					});
				}
			},
			// 拖动开始，记录一下偏移量
			touchstart: function(e) {
				var touch = e.touches[0] || e.changedTouches[0];
				this.deviationTop = touch.clientY - this.top;
				// console.log(this.deviationTop);
			},
			// 上下拖动时 
			touchmove: function(e) {
				var touch = e.touches[0] || e.changedTouches[0];
				var top = touch.clientY;
				top = top - this.deviationTop;
				if (top < 0) {
					top = 0;
				}
				if (top > this.windowHeight - 40) {
					top = this.windowHeight - 40;
				}
				this.top = top;
				return false;
			},
		}
	};
</script>

<style>
	/* 遮罩 */
	.mask {
		position: fixed;
		width: 100%;
		height: 100%;
		top: 0;
		left: 0;
		z-index: 99;
		background: rgba(248, 248, 248, 0.8);
	}

	/* 总盒子 */
	.major-box {
		border: 1px 0 solid;
		z-index: 100;
		position: fixed;
		bottom: 20%;
		right: 0;
		transition: left 0.5s;
		overflow: hidden;
	}

	.click-btn,
	.nav-box {
		float: left;
	}

	/* 按钮样式 */
	.nav-box {
		background-color: #FFF;
		border-radius: 0 0 0 5px;
	}

	.click-btn {
		width: 100px;
		height: 40px;
		background-color: #999;
		color: #fff;
		opacity: 0.8;
		text-align: center;
		border-radius: 50px 0 0 50px;
		padding: 6px 0;
	}

	.click-btn uni-view {
		line-height: 40px;
		font-size: 14px;
	}

	.click-btn view {
		padding-left: 8px;
	}

	/* 按钮盒子 */
	.nav-box {
		display: flex;
		flex-wrap: wrap;
		text-align: center;
		justify-content: center;
		background-color: #999;
		color: #fff;
		opacity: 0.8;
		text-align: center;
		border-radius: 50px 0 0 50px;
		padding: 5px 0;
	}

	.nav-btn {
		flex: 1;
		border: 0px #000 solid;
		min-width: 75px;
	}

	.icon {
		margin: 0 auto;
		width: 20px;
		height: 20px;
	}

	.nav-text {
		font-size: 14px;
	}
</style>
