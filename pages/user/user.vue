<template>
	<view class="container">
		<view class="user-section">
			<image class="bg" src="/static/user-bg.jpg"></image>
			<view class="user-info-box">
				<view class="portrait-box">
					<image class="portrait" :src="userInfo.portrait || '/static/missing-face.png'"></image>
				</view>
				<view class="info-box">
					<text class="username">{{userInfo.nickname || '游客'}}</text>
				</view>
			</view>
		</view>
		<view class="cover-container">
			<view class="tj-sction">
				<view class="tj-item">
					<text class="num">128.8</text>
					<text>余额</text>
				</view>
				<view class="tj-item">
					<text class="num">0</text>
					<text>优惠券</text>
				</view>
				<view class="tj-item">
					<text class="num">20</text>
					<text>积分</text>
				</view>
			</view>
			<!-- 订单 -->
			<view class="order-section">
				<view class="order-item" @click="navTo('/pages/order/order?state=0')" hover-class="common-hover"  :hover-stay-time="50">
					<text class="yticon icon-shouye"></text>
					<text>全部订单</text>
				</view>
				<view class="order-item" @click="navTo('/pages/order/order?state=1')"  hover-class="common-hover" :hover-stay-time="50">
					<text class="yticon icon-daifukuan"></text>
					<text>待付款</text>
				</view>
				<view class="order-item" @click="navTo('/pages/order/order?state=2')" hover-class="common-hover"  :hover-stay-time="50">
					<text class="yticon icon-yishouhuo"></text>
					<text>待收货</text>
				</view>
				<view class="order-item" @click="navTo('/pages/order/order?state=4')" hover-class="common-hover"  :hover-stay-time="50">
					<text class="yticon icon-shouhoutuikuan"></text>
					<text>退款/售后</text>
				</view>
			</view>
			<view class="list-section">
				<list-cell icon="icon-iconfontweixin" iconColor="#e07472" title="我的钱包" tips="您的会员还有3天过期"></list-cell>
				<list-cell icon="icon-dizhi" iconColor="#5fcda2" title="地址管理" @eventClick="navTo('/pages/address/address')"></list-cell>
				<list-cell icon="icon-share" iconColor="#9789f7" :title="'分享'" :tips="'邀请好友赢10万大礼'"></list-cell>
				<list-cell icon="icon-shoucang_xuanzhongzhuangtai" iconColor="#54b4ef" title="我的收藏"></list-cell>
				<list-cell icon="icon-shezhi1" iconColor="#e07472" title="设置" border="" @eventClick="navTo('/pages/set/set')"></list-cell>
			</view>
		</view>	
	</view>
</template>

<script>
	import listCell from '@/components/mix-list-cell/mix-list-cell.vue';
	export default {
		components: {
			listCell
		},
		data() {
			return {
				
			}
		},
		methods: {
			navTo() {
				
			}
		}
	}
</script>

<style lang='scss'>
	.container{
		background: #F5F5F5;
	}
	.user-section{
		height: 520upx;
		padding: 100upx 30upx 0;
		position:relative;
		.bg{
			position:absolute;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			filter: blur(1px);
			opacity: .7;
		}
		.user-info-box{
			height: 180upx;
			display:flex;
			align-items:center;
			position:relative;
			z-index: 1;
			.portrait{
				width: 130upx;
				height: 130upx;
				border:5upx solid #fff;
				border-radius: 50%;
			}
			.username{
				font-size: $font-lg + 6upx;
				color: $font-color-dark;
				margin-left: 20upx;
			}
		}

	}
	.cover-container{
		background: $page-color-base;
		margin-top: -150upx;
		padding: 0 30upx;
		position:relative;
		background: #f5f5f5;
		padding-bottom: 20upx;
		.tj-sction{
			@extend %section;
			.tj-item{
				@extend %flex-center;
				flex-direction: column;
				height: 140upx;
				font-size: $font-sm;
				color: #75787d;
			}
			.num{
				font-size: $font-lg;
				color: $font-color-dark;
				margin-bottom: 8upx;
			}
		}
		.order-section{
			@extend %section;
			padding: 28upx 0;
			margin-top: 20upx;
			.order-item{
				@extend %flex-center;
				width: 120upx;
				height: 120upx;
				border-radius: 10upx;
				font-size: $font-sm;
				color: $font-color-dark;
			}
			.yticon{
				font-size: 48upx;
				margin-bottom: 18upx;
				color: #fa436a;
			}
			.icon-shouhoutuikuan{
				font-size:44upx;
			}
		}
		.list-section{
			background: #fff;
			margin-top: 20upx;
			border-radius: 10upx;
		}
	}
	
	%flex-center {
		 display:flex;
		 flex-direction: column;
		 justify-content: center;
		 align-items: center;
		}
	%section {
		  display:flex;
		  justify-content: space-around;
		  align-content: center;
		  background: #fff;
		  border-radius: 10upx;
	}
</style>
