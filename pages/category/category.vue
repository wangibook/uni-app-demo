<template>
	<view class="content">
		<scroll-view scroll-y class="left-aside">
			<view v-for="item in flist" :key="item.id" class="f-item b-b" @click="tabtap(item)" :class="{active: item.id === currentId}">
				{{item.name}}
			</view>
		</scroll-view>
		<scroll-view scroll-with-animation scroll-y class="right-aside" @scroll="asideScroll" :scroll-top="tabScrollTop">
			<view v-for="item in slist" :key="item.id" class="s-list" :id="'main-'+item.id">
				<text class="s-item">{{item.name}}</text>
				<view class="t-list">
					<block  v-for="titem in tlist" :key="titem.id">
						<view class="t-item" v-if="item.id === titem.pid">
							<image :src="titem.picture"></image>
							<text>{{titem.name}}</text>
						</view>
					</block>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				sizeCalcState: false,
				currentId: 1,
				tabScrollTop: 0,
				flist: [],
				slist: [],
				tlist: []
			}
		},
		onLoad(){
			this.loadData();
		},
		methods: {
			async loadData(){
				let list = await this.$api.json('cateList');
				list.forEach(item=>{
					if(!item.pid){
						this.flist.push(item);  //pid为父级id, 没有pid或者pid=0是一级分类
					}else if(!item.picture){
						this.slist.push(item); //没有图的是2级分类
					}else{
						this.tlist.push(item); //3级分类
					}
				}) 
			},
			tabtap(item) {
				this.currentId = item.id;
				let index = this.slist.findIndex(sitem=>sitem.pid === item.id);
				console.log(this.slist[index])
				this.tabScrollTop = this.slist[index].top;
				console.log(this.tabScrollTop)
			},
			//右侧栏滚动
			asideScroll(e) {
				if(!this.sizeCalcState){
					this.calcSize();
				}
			},
			//计算右侧栏每个tab的高度等信息
			calcSize() {
				let h = 0;
				this.slist.forEach(item => {
					let view = uni.createSelectorQuery().select('main'+item.id)
					console.log(view)
				})
			}
			
		}
	}
</script>

<style lang='scss'>
	.content {
		height: 100%;
		background-color: #f8f8f8;
		display: flex;
		.left-aside {
			flex-shrink: 0;
			width: 200upx;
			height: 100%;
			background-color: #fff;
			.f-item {
				display: flex;
				align-items: center;
				justify-content: center;
				width: 100%;
				height: 100upx;
				font-size: 28upx;
				color: $font-color-base;
				position: relative;
				&.active{
					color: $base-color;
					background: #f8f8f8;
					&:before{
						content: '';
						position: absolute;
						left: 0;
						top: 50%;
						transform: translateY(-50%);
						height: 36upx;
						width: 8upx;
						background-color: $base-color;
						border-radius: 0 4px 4px 0;
						opacity: .8;
					}
				}
			}
		}
		.right-aside{
			flex: 1;
			overflow: hidden;
			padding-left: 20upx;
			.s-item{
				display: flex;
				align-items: center;
				height: 70upx;
				padding-top: 8upx;
				font-size: 28upx;
				color: $font-color-dark;
			}
			.t-list{
				display: flex;
				flex-wrap: wrap;
				width: 100%;
				background: #fff;
				padding-top: 12upx;
				&:after{
					content: '';
					flex: 99;
					height: 0;
				}
				.t-item{
					flex-shrink: 0;
					display: flex;
					justify-content: center;
					align-items: center;
					flex-direction: column;
					width: 176upx;
					font-size: 26upx;
					color: #666;
					padding-bottom: 20upx;
					image{
						width: 140upx;
						height: 140upx;
					}
				}
			}
		}
	}
</style>
