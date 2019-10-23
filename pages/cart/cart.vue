<template>
	<view class="container">
		<view v-if="empty" class="empty">
			<image src="/static/emptyCart.jpg" mode="aspectFit"></image>
			<view class="empty-tips">
				空空如也
				<navigator class="navigator" url="../index/index" open-type="switchTab">随便逛逛></navigator>
			</view>
		</view>
		<view class="cart-list" v-else>
			<view class="list-item" v-for="(item,index) in cartList" :key="index">
				<view class="yticon icon-xuanzhong2 checkbox"></view>
				<view class="goods-info">
					<view class="item-img">
						<image :src="item.image" ></image>
					</view>
					<view class="item-right">
						<view class="goods-title">{{item.title}}</view>
						<view class="goods-label">{{item.attr_val}}</view>
						<view class="goods-price">¥ {{item.price}}</view>
						<view class="buy-num">
							<view class="jian-btn" @click="jianBtnTap">-</view>
							<input type="number" value="1" disabled/>
							<view class="jia-btn" @click="jiaBtnTap">+</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	// import uniNumberBox from '@/components/uni-number-box/uni-number-box.vue'
	export default {
		data() {
			return {
				empty: true,
				cartList: [
					{
						id: 1,
						image: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553005139&di=3368549edf9eee769a9bcb3fbbed2504&imgtype=jpg&er=1&src=http%3A%2F%2Fimg002.hc360.cn%2Fy3%2FM01%2F5F%2FDB%2FwKhQh1T7iceEGRdWAAAAADQvqk8733.jpg',
						attr_val: '春装款 L',
						stock: 15,
						title: 'OVBE 长袖风衣',
						price: 278.00,
						number: 1
					},
					{
						id: 1,
						image: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553005139&di=3368549edf9eee769a9bcb3fbbed2504&imgtype=jpg&er=1&src=http%3A%2F%2Fimg002.hc360.cn%2Fy3%2FM01%2F5F%2FDB%2FwKhQh1T7iceEGRdWAAAAADQvqk8733.jpg',
						attr_val: '春装款 L',
						stock: 15,
						title: 'OVBE 长袖风衣',
						price: 278.00,
						number: 1
					}
				]
			}
		},
		methods: {
			jianBtnTap(e) {
				console.log(e)
			}
		}
	}
</script>

<style lang='scss'>
	.container{
		padding-bottom: 134upx;
		/* 空白页 */
		.empty{
			position:fixed;
			left: 0;
			top:0;
			width: 100%;
			height: 100vh;
			padding-bottom:100upx;
			display:flex;
			justify-content: center;
			flex-direction: column;
			align-items:center;
			background: #fff;
			image{
				width: 240upx;
				height: 160upx;
				margin-bottom:30upx;
			}
			.empty-tips{
				display:flex;
				font-size: $font-sm+2upx;
				color: $font-color-disabled;
				.navigator{
					color: $uni-color-primary;
					margin-left: 16upx;
				}
			}
		}
		.cart-list{
			.list-item{
				height: 150upx;
				display: flex;
				justify-content: space-between;
				margin-bottom: 20upx;
				box-sizing: border-box;
				border-bottom: 1px solid #ccc;
				.checkbox{
					width: 80upx;
					height: 150upx;
					line-height: 150upx;
					text-align: center;
					font-size: 40upx;
				}
				.goods-info{
					flex: 1;
					display: flex;
					justify-content: space-between;
					.item-img{
						width: 130upx;
						 height: 130upx;
						 overflow: hidden;
						 margin-right: 20upx;
					}
					.item-right{
						flex: 1;
						position: relative;
						.goods-title{
							font-size:$font-base + 2upx;
							color: $font-color-dark;
						}
						.goods-label{
							font-size: $font-sm + 2upx;
							color: $font-color-light;
						}
						.goods-price{
							font-size:$font-base + 2upx;
							color: #b5272d;
						}
						.buy-num{
							width: 164rpx;
						    height: 48rpx;
						    line-height: 48rpx;
						  position: absolute;
						  right: 30rpx;
						  bottom: 0;
						  display: flex;
						  font-size: 24rpx;
						  text-align: center;
							.jian-btn{
								width: 48rpx;
							    height: 100%;
							    border-left: 1rpx solid #ccc;
							    border-bottom: 1rpx solid #ccc;
							    border-top: 1rpx solid #ccc;
							    border-bottom-left-radius: 6rpx;
							    border-top-left-radius: 6rpx;
							}
							.jia-btn{
								width: 48rpx;
								  height: 100%;
								  border-right: 1rpx solid #ccc;
								  border-bottom: 1rpx solid #ccc;
								  border-top: 1rpx solid #ccc;
								  border-bottom-right-radius: 6rpx;
								  border-top-right-radius: 6rpx;
							}
							input{
								width: 68rpx;
								  height: 48rpx;
								  min-height: 48rpx;
								  text-align: center;
								  font-size: 24rpx;
								  border: 1rpx solid #ccc;
							}
						}
					}
				}
			}
			
			
		}
	}
</style>
