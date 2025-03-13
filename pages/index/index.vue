<template>
	<view>
		<view class="home">
			<swiper class="home__swiper" circular :autoplay="autoplay" :interval="2000" :indicator-dots="true">
				<swiper-item v-for="item in swiperList" :key="item.id">
					<view class="home__swiper__item">
						{{item.src}}
					</view>
				</swiper-item>

			</swiper>
			<view class="home__content">
				<view class="home__content__menu">
					<view class="home__content__menu__top">
						<image style="height: 80rpx;width: 80rpx;" src="/static/coffee.png" mode="aspectFit"></image>
						hello,来跟 睿行打个招呼！
					</view>
					<view class="home__content__menu__middle">
						<view class="menu__middle__item" v-for="(item, index) in actionList" :key="index" @click="onMenuTop(item)">
							<view>
								<image :src="item.pic" style="width: 100rpx; height: 100rpx;" mode=""></image>
							</view>
							<view class="menu__middle__item__title">{{item.titile}}</view>
							<view class="menu__middle__item__desc">{{item.discription}}</view>
						</view>
					</view>
					<view class="home__content__menu__bottom">
						<view class="menu__middle__item" v-for="(item, index) in marketList" :key="index"  @click="onMenuTop(item)">
							<view>
								<image :src="item.pic" style="width: 100rpx; height: 100rpx;" mode=""></image>
							</view>
							<view class="menu__middle__item__title">{{item.titile}}</view>
							<view class="menu__middle__item__desc">{{item.discription}}</view>
						</view>
					</view>
				</view>
				<view class="home__content__banner">
					<image src="/static/homebanner.png" style="height: ;width: 100%;" mode="widthFix"></image>
					<!-- 点击事件应该是position加上去的，就不加view去写样式了，应该就一个页面跳转 -->
					<!--  -->
				</view>
			</view>
			
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				autoplay: true,
				// 轮播图列表
				swiperList: [{
					src: "这里是swiper1",
					id: 1,
				}, {
					src: "这里是swiper2",
					id: 2
				}, {
					src: "这里是swiper3",
					id: 3
				}],
				// 头部窗口列表
				actionList: [{
					pic: "../../static/online-buy.png",
					titile: "到店取",
					discription: "提前点免排队"
				}, {
					pic: "../../static/luck-send.png",
					titile: "幸运送",
					discription: "外卖及时送达"
				}, {
					pic: "../../static/dianshang-buy.png",
					titile: "电商购",
					discription: "囤咖啡买周边"
				}],
				marketList: [{
					pic: "../../static/market1.png",
					titile: "轻轻茉莉",
					discription: "现催升级"
				}, {
					pic: "../../static/market2.png",
					titile: "礼品卡",
					discription: "送TA咖啡"
				}, {
					pic: "../../static/market3.png",
					titile: "多人团聚",
					discription: "一键开票"
				}, {
					pic: "../../static/market4.png",
					titile: "拼单减满",
					discription: "一起点更划算"
				}]
			}
		},
		methods: {
			onMenuTop(item) {
				console.log(item);
			}
		}
	}
</script>

<style lang="scss">
	.home {
		// padding: 20px;
		// font-size: 14px;
		// line-height: 24px;
		height: 100%;

		.home__swiper {
			height: 580rpx;

			.home__swiper__item {
				height: 100%;
				width: 100%;
				display: flex;
				justify-content: center;
				align-items: center;

				&:nth-child(1) {
					background-color: #b9cef5;
				}

				&:nth-child(2) {
					background-color: #a7f5b7;
				}

				&:nth-child(3) {
					background-color: #f5a9c1;
				}
			}
		}

		.home__content {
			background-color: #F5F5F4;
			padding: 0 20rpx;
			height: 100%;
			background-color: white;

			>.home__content__menu {
				height: 500rpx;
				width: 100%;
				border-radius: 10rpx;
				margin-top: -10rpx;
				position: relative;
				top: -10rpx;

				>.home__content__menu__top {
					background-color: #2B2F34;
					height: 80rpx;
					border-radius: 10rpx 10rpx 0 0;
					padding: 0 30rpx;
					display: flex;
					align-items: center;
					color: #CE9259;
					font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
				}

				>.home__content__menu__middle {
					display: flex;
					justify-content: space-between;
					align-items: center;
					height: 205rpx;
					text-align: center;
					padding: 0 10rpx;

					.menu__middle__item {
						width: 250rpx;

						.menu__middle__item__title {
							font-weight: bold;
							letter-spacing: 5rpx;
						}

						.menu__middle__item__desc {
							margin-top: 10rpx;
							font-size: 20rpx;
							color: gray;
						}
					}

				}

				>.home__content__menu__bottom {
					display: flex;
					justify-content: space-between;
					align-items: center;
					height: 205rpx;
					text-align: center;
					padding: 0 10rpx;

					.menu__middle__item {
						width: 250rpx;

						.menu__middle__item__title {
							font-weight: bold;
							letter-spacing: 5rpx;
						}

						.menu__middle__item__desc {
							margin-top: 10rpx;
							font-size: 20rpx;
							color: gray;
						}
					}

				}
			}
			>.home__content__banner{
				border-radius: 10rpx;
			}
		}
	}
</style>