<template>
	<view class="content">
		<view class="mp-search-box">
			<input class="ser-input" type="text" value="输入关键字搜索" />
		</view>
		<!-- 头部轮播图 -->
		<view class="carousel-section">
			<swiper class="carousel"   autoplay=true indicator-dots>
				<swiper-item class="carousel-item" v-for="(item, index) in carouselList" :key="index">
					<image :src="item.src" />
				</swiper-item>
			</swiper>
		</view>
		<!-- 分类 -->
		<view class="cate-section">
			<view class="cate-item">
				<image src="/static/temp/c3.png"></image>
				<text>环球美食</text>
			</view>
			<view class="cate-item">
				<image src="/static/temp/c5.png"></image>
				<text>个护美妆</text>
			</view>
			<view class="cate-item">
				<image src="/static/temp/c6.png"></image>
				<text>营养保健</text>
			</view>
			<view class="cate-item">
				<image src="/static/temp/c7.png"></image>
				<text>家居厨卫</text>
			</view>
			<view class="cate-item">
				<image src="/static/temp/c8.png"></image>
				<text>速食生鲜</text>
			</view>
		</view>
		<view class="ad-1">
			<image src="/static/temp/ad1.jpg" mode="scaleToFill"></image>
		</view>
		<!-- 秒杀楼层 -->
		<view class="seckill-section m-t">
			<view class="s-header">
				<image class="s-img" src="/static/temp/secskill-img.jpg" mode="widthFix"></image>
				<text class="tip">8点场</text>
				<text class="hour timer">07</text>
				<text class="minute timer">13</text>
				<text class="second timer">55</text>
				<text class="yticon icon-you"></text>
			</view>
			<scroll-view class="floor-list" scroll-x>
				<view class="scoll-wrapper">
					<view class="floor-item" v-for="(item, index) in goodsList" :key="index" @click="navToDetailPage(item)">
						<image :src="item.image3" mode="aspectFill"></image>
						<text class="title clamp">{{item.title}}</text>
						<text class="price">￥{{item.price}}</text>
					</view>
				</view>
			</scroll-view>
		</view>
		<!-- 精品团购 -->
		<view class="f-header m-t">
			<image src="/static/temp/h1.png"></image>
			<view class="tit-box">
				<text class="tit">精品团购</text>
				<text class="tit2">Boutique Group Buying</text>
			</view>
			<text class="yticon icon-you"></text>
		</view>
		<view class="group-section">
			<swiper class="g-swiper" :duration="500">
				<swiper-item
					class="g-swiper-item"
					v-for="(item, index) in goodsList" :key="index"
					@click="navToDetailPage(item)">
					<view class="g-item left">
						<image :src="item.image" mode="aspectFill"></image>
						<view class="t-box">
							<text class="title clamp">{{item.title}}</text>
							<view class="price-box">
								<text class="price">￥{{item.price}}</text> 
								<text class="m-price">￥188</text> 
							</view>
							<view class="pro-box">
								<view class="progress-box">
									<progress percent="72" activeColor="#fa436a" active stroke-width="6" />
								</view>
								<text>6人成团</text>
							</view>
						</view>	
					</view>
				</swiper-item>
			</swiper>
		</view>
		<!-- 分类推荐楼层 -->
			<view class="f-header m-t">
				<image src="/static/temp/h1.png"></image>
				<view class="tit-box">
					<text class="tit">分类精选</text>
					<text class="tit2">Competitive Products For You</text>
				</view>
				<text class="yticon icon-you"></text>
			</view>
			<view class="hot-floor">
				<view class="floor-img-box">
					<image class="floor-img" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553409398864&di=4a12763adccf229133fb85193b7cc08f&imgtype=0&src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201703%2F19%2F20170319150032_MNwmn.jpeg" mode="scaleToFill"></image>
				</view>
				<scroll-view class="floor-list" scroll-x>
					<view class="scoll-wrapper">
						<view 
							v-for="(item, index) in goodsList" :key="index"
							class="floor-item"
							@click="navToDetailPage(item)"
						>
							<image :src="item.image" mode="aspectFill"></image>
							<text class="title clamp">{{item.title}}</text>
							<text class="price">￥{{item.price}}</text>
						</view>
						<view class="more">
							<text>查看全部</text>
							<text>More+</text>
						</view>
					</view>
				</scroll-view>
			</view>
			<view class="hot-floor">
				<view class="floor-img-box">
					<image class="floor-img" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553409984228&di=dee176242038c2d545b7690b303d65ea&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2F5ef4da9f17faaf4612f0d5046f4161e556e9bbcfdb5b-rHjf00_fw658" mode="scaleToFill"></image>
				</view>
				<scroll-view class="floor-list" scroll-x>
					<view class="scoll-wrapper">
						<view 
							v-for="(item, index) in goodsList" :key="index"
							class="floor-item"
							@click="navToDetailPage(item)"
						>
							<image :src="item.image3" mode="aspectFill"></image>
							<text class="title clamp">{{item.title}}</text>
							<text class="price">￥{{item.price}}</text>
						</view>
						<view class="more">
							<text>查看全部</text>
							<text>More+</text>
						</view>
					</view>
				</scroll-view>
			</view>
			<view class="hot-floor">
				<view class="floor-img-box">
					<image class="floor-img" src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1553409794730&di=12b840ec4f5748ef06880b85ff63e34e&imgtype=0&src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F01dc03589ed568a8012060c82ac03c.jpg%40900w_1l_2o_100sh.jpg" mode="scaleToFill"></image>
				</view>
				<scroll-view class="floor-list" scroll-x>
					<view class="scoll-wrapper">
						<view 
							v-for="(item, index) in goodsList" :key="index"
							class="floor-item"
							@click="navToDetailPage(item)"
						>
							<image :src="item.image2" mode="aspectFill"></image>
							<text class="title clamp">{{item.title}}</text>
							<text class="price">￥{{item.price}}</text>
						</view>
						<view class="more">
							<text>查看全部</text>
							<text>More+</text>
						</view>
					</view>
				</scroll-view>
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				carouselList: [], // 轮播列表
				goodsList: [],  // 商品列表
			}
		},
		onLoad() {
			this.loadData();
		},
		methods: {
			async loadData() {
				this.carouselList = await this.$api.json('carouselList');
				let goodsList = await this.$api.json('goodsList');
				this.goodsList = goodsList || [];
			},
			//详情页
			navToDetailPage(item) {
				//测试数据没有写id，用title代替
				let id = item.id;
				uni.navigateTo({
					url: `/pages/goods-detail/goods-detail?id=${id}`
				})
			},
		}
	}
</script>

<style lang="scss">
	.m-t{
		margin-top: 16upx;
	}
	.title{
		font-size: $font-lg;
		color: $font-color-dark;
		line-height: 80upx;
	}
	.price{
		font-size: $font-lg;
		color: $uni-color-primary;
		line-height: 1;
	}
	.content {
		.mp-search-box{
			position:absolute;
			left: 0;
			top: 30upx;
			z-index: 9999;
			width: 100%;
			padding: 0 80upx;
			.ser-input{
				flex:1;
				height: 56upx;
				line-height: 56upx;
				text-align: left;
				padding-left: 20upx;
				font-size: 28upx;
				color:$font-color-base;
				border-radius: 20px;
				background: rgba(255,255,255,.6);
			}
		}
		.carousel-section{
			width: 100%;
			.carousel{
				.carousel-item{
					image{
						width: 100%;
						height: 100%;
					}
				}
			}
		}
		/* 分类 */
		.cate-section {
			display: flex;
			justify-content: space-around;
			align-items: center;
			flex-wrap:wrap;
			padding: 30upx 22upx; 
			background: #fff;
			.cate-item {
				display: flex;
				flex-direction: column;
				align-items: center;
				font-size: $font-sm + 2upx;
				color: $font-color-dark;
			}
			/* 原图标颜色太深,不想改图了,所以加了透明度 */
			image {
				width: 88upx;
				height: 88upx;
				margin-bottom: 14upx;
				border-radius: 50%;
				opacity: .7;
				box-shadow: 4upx 4upx 20upx rgba(250, 67, 106, 0.3);
			}
		}
		.ad-1{
			width: 100%;
			height: 210upx;
			padding: 10upx 0;
			background: #fff;
			image{
				width:100%;
				height: 100%; 
			}
		}
		/* 秒杀专区 */
		.seckill-section{
			padding: 4upx 30upx 24upx;
			background: #fff;
			.s-header{
				display:flex;
				align-items:center;
				height: 92upx;
				line-height: 1;
				.s-img{
					width: 140upx;
					height: 30upx;
				}
				.tip{
					font-size: $font-base;
					color: $font-color-light;
					margin: 0 20upx 0 40upx;
				}
				.timer{
					display:inline-block;
					width: 40upx;
					height: 36upx;
					text-align:center;
					line-height: 36upx;
					margin-right: 14upx;
					font-size: $font-sm+2upx;
					color: #fff;
					border-radius: 2px;
					background: rgba(0,0,0,.8);
				}
				.icon-you{
					font-size: $font-lg;
					color: $font-color-light;
					flex: 1;
					text-align: right;
				}
			}
			.floor-list{
				white-space: nowrap;
			}
			.scoll-wrapper{
				display:flex;
				align-items: flex-start;
			}
			.floor-item{
				width: 150upx;
				margin-right: 20upx;
				font-size: $font-sm+2upx;
				color: $font-color-dark;
				line-height: 1.8;
				image{
					width: 150upx;
					height: 150upx;
					border-radius: 6upx;
				}
				.price{
					color: $uni-color-primary;
				}
			}
		}
		/* 团购楼层 */
		.group-section{
			background: #fff;
			.g-swiper{
				height: 650upx;
				padding-bottom: 30upx;
			}
			.g-swiper-item{
				width: 100%;
				padding: 0 30upx;
				display:flex;
			}
			image{
				width: 100%;
				height: 400upx;
				border-radius: 4px;
			}
			.g-item{
				display:flex;
				flex-direction: column;
				overflow:hidden;
			}
			.left{
				flex: 1.2;
				margin-right: 24upx;
				.t-box{
					padding-top: 20upx;
				}
			}
			.t-box{
				height: 160upx;
				font-size: $font-base+2upx;
				color: $font-color-dark;
				line-height: 1.6;
			}
			.price{
				color:$uni-color-primary;
			}
			.m-price{
				font-size: $font-sm+2upx;
				text-decoration: line-through;
				color: $font-color-light;
				margin-left: 8upx;
			}
			.pro-box{
				display:flex;
				align-items:center;
				margin-top: 10upx;
				font-size: $font-sm;
				color: $font-base;
				padding-right: 10upx;
			}
			.progress-box{
				flex: 1;
				border-radius: 10px;
				overflow: hidden;
				margin-right: 8upx;
			}
		}
		/* 分类推荐楼层 */
		.hot-floor{
			width: 100%;
			overflow: hidden;
			margin-bottom: 20upx;
			.floor-img-box{
				width: 100%;
				height:320upx;
				position:relative;
				&:after{
					content: '';
					position:absolute;
					left: 0;
					top: 0;
					width: 100%;
					height: 100%;
					background: linear-gradient(rgba(255,255,255,.06) 30%, #f8f8f8);
				}
			}
			.floor-img{
				width: 100%;
				height: 100%;
			}
			.floor-list{
				white-space: nowrap;
				padding: 20upx;
				padding-right: 50upx;
				border-radius: 6upx;
				margin-top:-140upx;
				margin-left: 30upx;
				background: #fff;
				box-shadow: 1px 1px 5px rgba(0,0,0,.2);
				position: relative;
				z-index: 1;
			}
			.scoll-wrapper{
				display:flex;
				align-items: flex-start;
			}
			.floor-item{
				width: 180upx;
				margin-right: 20upx;
				font-size: $font-sm+2upx;
				color: $font-color-dark;
				line-height: 1.8;
				image{
					width: 180upx;
					height: 180upx;
					border-radius: 6upx;
				}
				.price{
					color: $uni-color-primary;
				}
			}
			.more{
				display:flex;
				align-items: center;
				justify-content: center;
				flex-direction: column;
				flex-shrink: 0;
				width: 180upx;
				height: 180upx;
				border-radius: 6upx;
				background: #f3f3f3;
				font-size: $font-base;
				color: $font-color-light;
				text:first-child{
					margin-bottom: 4upx;
				}
			}
		}
		.f-header{
			display:flex;
			align-items:center;
			height: 140upx;
			padding: 6upx 30upx 8upx;
			background: #fff;
			image{
				flex-shrink: 0;
				width: 80upx;
				height: 80upx;
				margin-right: 20upx;
			}
			.tit-box{
				flex: 1;
				display: flex;
				flex-direction: column;
			}
			.tit{
				font-size: $font-lg +2upx;
				color: $font-color-dark;
				line-height: 1.3;
			}
			.tit2{
				font-size: $font-sm;
				color: $font-color-light;
			}
			.icon-you{
				font-size: $font-lg +2upx;
				color: $font-color-light;
			}
		}
	}
	
</style>
