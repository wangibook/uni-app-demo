<template>
	<view class="mask" v-if="show">
		<view class="mask-content">
			<scroll-view class="view-content" scroll-y>
				<view class="share-header">
					分享到
				</view>
				<view class="share-list">
					<view 
						v-for="(item, index) in shareList" :key="index"
						class="share-item" 
						@click="shareToFriend(item.text)"
					>
						<image :src="item.icon" mode=""></image>
						<text>{{item.text}}</text>
					</view>
				</view>
			</scroll-view>
			<view class="bottom b-t" @click="toggleMask">取消</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			shareList: Array
		},
		data() {
			return {
				show: false
			}
		},
		methods: {
			toggleMask() {
				this.show = !this.show
			}
		}
	}
</script>

<style lang='scss'>
	.mask{
		position:fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		display:flex;
		justify-content: center;
		align-items: flex-end;
		z-index: 998;
		background-color: rgba(0,0,0,.4);
		transition: .3s;
		.bottom{
			position:absolute;
			left: 0;
			bottom: 0;
			display:flex;
			justify-content: center;
			align-items: center;
			width: 100%;
			height: 90upx;
			background: #fff;
			z-index: 9;
			font-size: $font-base + 2upx;
			color: $font-color-dark;
		}
	}
	
	.mask-content{
		width: 100%;
		height: 580upx;
		transition: .3s;
		background: #fff;
		&.has-bottom{
			padding-bottom: 90upx;
		}
		.view-content{
			height: 100%;
		}
	}
	.share-header{
		height: 110upx;
		font-size: $font-base+2upx;
		color: font-color-dark;
		display:flex;
		align-items:center;
		justify-content: center;
		padding-top: 10upx;
		&:before, &:after{
			content: '';
			width: 240upx;
			heighg: 0;
			border-top: 1px solid $border-color-base;
			transform: scaleY(.5);
			margin-right: 30upx;
		}
		 &:after{
			 margin-left: 30upx;
			 margin-right: 0;
		 }
	}
	.share-list{
		display:flex;
		flex-wrap: wrap;
	}
	.share-item{
		min-width: 33.33%;
		display:flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 180upx;
		image{
			width: 80upx;
			height: 80upx;
			margin-bottom: 16upx;
		}
		text{
			font-size: $font-base;
			color: $font-color-base;
		}
	}
</style>
