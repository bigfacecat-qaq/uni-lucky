<template>
	<view class="menu">
		<!-- 空出顶部距离 -->
		<view class="menu__top" :style="{marginTop:searchBarTop + 'px',height:searchBarHeight + 'px'}">
			<view class="menu__top__method">
				<view class="menu__top__method__item" v-for="(item, index) in topMenuList" :key="index"
					:class="{'menu__top__method__item--active':item.selected}" @click="onChangeMethod(item)">
					{{item.text}}
				</view>
			</view>
			<view class="menu__top__search">
				<u--input placeholder="新鲜现催乌龙" v-model="searchVal" shape="circle"
					:customStyle="{height:'33rpx', width: '270rpx', marginLeft: '10rpx'}" prefixIcon="search"
					prefixIconStyle="font-size: 22px;color: #909399"></u--input>
			</view>
		</view>
		<view class="menu__position">
			<view class="menu__position__define">
				<u-icon name="map"></u-icon>
				{{'花果山水帘洞'}}
			</view>
			<view>
				<u-button text="月落" shape="circle" plain><u-icon name="photo"></u-icon>拼单</u-button>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchBarTop: 0, //搜索栏的外边框高度，单位px
				searchBarHeight: 0, //搜索栏的高度，单位px

				topMenuList: [{
						text: "自提",
						selected: true,
					},
					{
						text: "外卖",
						selected: false
					}
				],

				searchVal: "",
			}
		},

		methods: {
			onChangeMethod(e) {
				console.log(e);
				this.topMenuList.forEach(item => {
					item.text === e.text ? (item.selected = true) : (item.selected = false)
				})
			}
		},

		onLoad() {
			let menuButtonInfo = uni.getMenuButtonBoundingClientRect();
			this.searchBarTop = menuButtonInfo.top;
			this.searchBarHeight = menuButtonInfo.height;
		}
	}
</script>

<style lang="scss">
	.menu {
		.menu__top {
			display: flex;
			padding: 0 20rpx;
			align-items: center;

			.menu__top__method {
				display: flex;
				width: 150rpx;
				background-color: #d1d1d1;
				border-radius: 20rpx;
				height: 80%;
				justify-content: space-around;
				font-size: 27rpx;
				align-items: center;

				.menu__top__method__item {
					width: 80rpx;
					border-radius: 20rpx;
					display: flex;
					justify-content: center;
					align-items: center;
					height: 100%;
				}

				.menu__top__method__item--active {
					background-color: blue;
					color: white
				}
			}
		}

		.menu__position {
			height: 100rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			box-shadow: 0px 4px 8px -3px #847976;
			margin: 1rpx 20rpx 0 20rpx;
			
			.menu__position__define {
				display: flex;
			}
		}

	}
</style>