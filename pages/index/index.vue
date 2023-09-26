<template>
	<view>
		<view>
			<uni-row style="margin: 30rpx 20rpx 10rpx 30rpx;">
				<uni-col :span="12">
					<view>
						<image style="max-height: 90rpx;" mode="heightFix" src="/static/web/top-logo.png"></image>
					</view>
				</uni-col>
				<uni-col :span="12">
					<view style="display: flex;flex-direction: row;justify-content:flex-end;">
						<image @click="toggle()" style="max-height: 50rpx;top:20rpx; " mode="heightFix"
							src="/static/web/menu.png">
						</image>
					</view>
				</uni-col>
			</uni-row>
		</view>
		<view style="margin:0 4% 0% 2%;height: auto;">
			<uni-swiper-dot :info="info" :current="current" field="content" :mode="mode">
				<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" @change="change" next-margin="0"
					circular="true">
					<swiper-item v-for="(item, index) in info" :key="index">
						<view class="swiper-item align-center">
							<image class="swiper-img" mode="widthFix" :src="item.content"  @load="recalculateHeight()"></image>
						</view>
					</swiper-item>
				</swiper>
			</uni-swiper-dot>
		</view>

		<view class="mar-30">
			<uni-title type="h1" title="应用介绍"></uni-title>
			<view class="card-info">
				<text class="introduciton">AndPods 是全网 3000万+
					下载量的“蓝牙耳机神器”，支持AirPods/Beats/华强北以及主流耳机品牌型号，具备耳机弹窗定制、自动音频控制、手势设置、语音播报、查找定位、个性化小组件/通知等丰富的功能，强化你的耳机在安卓端的使用体验。
				</text>
			</view>
		</view>

		<view class="mar-30">
			<uni-title type="h1" title="特色功能"></uni-title>
			<uni-row>
				<uni-col :span="12">
					<view class="card-info" style="margin:15rpx 15rpx 15rpx 0rpx">
						<image src="/static/svg/tanchuang.svg" class="img-icon"></image>
						<uni-title type="h3" title="特色功能"></uni-title>
						<text class="introduciton">自定义弹窗视频/GIF，1000+主题资源下载</text>
					</view>
				</uni-col>
				<uni-col :span="12">
					<view class="card-info" style="margin:15rpx 0rpx 15rpx 15rpx">
						<image src="/static/svg/music.svg" class="img-icon"></image>
						<uni-title type="h3" title="耳机增值功能"></uni-title>
						<text class="introduciton">自动音频控制、自定义手势设置、语音播报等</text>
					</view>
				</uni-col>
			</uni-row>
			<uni-row>
				<uni-col :span="12">
					<view class="card-info" style="margin:15rpx 15rpx 15rpx 0rpx">
						<image src="/static/svg/location.svg" class="img-icon"></image>
						<uni-title type="h3" title="辅助查找耳机"></uni-title>
						<text class="introduciton">定位最后一次连接位置，测距和发声查找</text>
					</view>
				</uni-col>
				<uni-col :span="12">
					<view class="card-info" style="margin:15rpx 0rpx 15rpx 15rpx">
						<image src="/static/svg/battery.svg" class="img-icon"></image>
						<uni-title type="h3" title="多样化电量显示"></uni-title>
						<text class="introduciton">支持桌面小组件、个性化通知辅助显示电量效果</text>
					</view>
				</uni-col>
			</uni-row>
		</view>
		<view class="mar-30" style="padding-bottom: 140rpx;">
			<uni-title type="h1" title="应用介绍"></uni-title>
			<uni-row>
				<uni-col :span="12">
					<view class="card-info" style="margin:15rpx 15rpx 15rpx 0rpx">
						<a href="//pd.qq.com/s/5yg7tg71v" class="social-a">
							<image src="/static/svg/qq.svg" style="max-width: 100rpx;max-height: 100rpx;"></image>
							<uni-title type="h3" title="QQ频道"></uni-title>
						</a>
					</view>
				</uni-col>
				<uni-col :span="12">
					<view class="card-info" style="margin:15rpx 15rpx 15rpx 0rpx">
						<a href="//support.qq.com/product/387882" class="social-a">
							<image src="/static/svg/shequ.svg" style="max-width: 100rpx;max-height: 100rpx;"></image>
							<uni-title type="h3" title="QQ频道"></uni-title>
						</a>
					</view>
				</uni-col>
			</uni-row>
		</view>

		<view class="mar-30 download-view">
			<a href="https://a.app.qq.com/o/simple.jsp?pkgname=cn.xiaolongonly.andpodsop" class="manu-a">
				<button class="download-btn">立即下载</button>
			</a>
		</view>


		<view style="display: flex;">
			<!-- 普通弹窗 -->
			<uni-popup ref="popup" background-color="#fff" style="">
				<view class="popup-content">
					<image style="padding: 50rpx 150rpx 150rpx 150rpx;" src="/static/web/andpods.png" class="img-icon">
					</image>
					<uni-list class="align-center">
						<a href="#/" class="manu-a"><uni-list-item title="主页"></uni-list-item></a>
						<a href="https://a.app.qq.com/o/simple.jsp?pkgname=cn.xiaolongonly.andpodsop"
							class="manu-a"><uni-list-item title="下载APP"></uni-list-item></a>
						<a href="https://www.andpods.cn/agreement" class="manu-a"><uni-list-item
								title="服务条款"></uni-list-item></a>
						<a href="https://www.andpods.cn/privacy" class="manu-a"><uni-list-item
								title="隐私政策"></uni-list-item></a>
					</uni-list>
				</view>
			</uni-popup>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info: [{
					content: '/static/screenshot/p6.png'
				}, {
					content: '/static/screenshot/p7.png'
				}, {
					content: '/static/screenshot/p8.png'
				}, {
					content: '/static/screenshot/p9.png'
				}, {
					content: '/static/screenshot/p10.png'
				}],
				current: 0,
				mode: 'round',
				swiperHeight: 500,
				scrollTop: 0,
				old: {
					scrollTop: 0
				}
			}
		},
		onLoad() {
			// this.recalculateHeight();
		},
		methods: {
			change(e) {
				this.current = e.detail.current;
			},
			recalculateHeight() {
				let query = uni.createSelectorQuery().in(this)
				query.selectAll(".swiper-img").boundingClientRect()
				query.exec(res => {
					if (res && res[0] && res[0][this.current]) {
						this.swiperHeight = res[0][this.current].height;
					}
				})
			},
			toggle(type) {
				this.$refs.popup.open("left")
			}
		}
	}
</script>

<style>
	.flex-item {
		width: 33.3%;
		text-align: center;
	}

	.swiper-box {
		min-height: 100%;
	}

	.swiper-item {
		max-height: 85vh;
		width: 100%;
	}

	.introduciton {
		font-size: 14px;
		min-height: 72px;
		color: rgba(61, 61, 61, 0.7);
	}

	.card-info {
		padding: 25rpx;
		border-radius: 30rpx;
		background-color: #f9f9fb;
	}

	.social-a {
		display: inline-flex;
		align-items: center;
		-webkit-box-align: center;
		justify-content: center;
		z-index: 1;
		text-decoration: none;
		font-size: 14px;
	}

	.img-icon {
		max-width: 100rpx;
		max-height: 100rpx;
	}

	.mar-30 {
		margin: 30rpx;
	}

	.swiper-img {
		height: 100%;
		border-radius: 30rpx;
	}

	.download-view {
		position: fixed;
		bottom: 0rpx;
		height: 100rpx;
		background: transparent;
		width: 90%;
	}

	.download-btn {
		background: linear-gradient(90deg, #1890FF 0%, #84C5FF 100%);
		color: #fff;
		height: 100%;
		border-radius: 50rpx;
		font-size: 40rpx;
		font-weight: 500;
	}

	.align-center {
		display: flex;
		align-items: center;
		flex-direction: column;
	}

	.popup-content {
		align-items: center;
		justify-content: center;
		padding: 15rpx;
		height: 100vh;
		box-shadow: 0 0 20rpx rgba(0, 0, 0, .5);
		-webkit-box-shadow: 0 0 20px rgba(0, 0, 0, .5);
	}

	.manu-a {
		text-decoration: none;
	}
</style>