<template>
	<view>
		<view class="goods-item">
			<!-- 商品左侧图片区域 -->
			<view class="goods-item-left">
				<radio color="#c00000" v-if="showRadio" :checked="goods.goods_state" @click="radioClickHandler"></radio>
				<image :src="goods.goods_small_logo || defaultPic" class="goods-pic"></image>
			</view>
			<!-- 商品右侧信息区域 -->
			<view class="goods-item-right">
				<!-- 商品标题 -->
				<view class="goods-name">{{goods.goods_name}}</view>
				<view class="goods-info-box">
					<!-- 商品价格 -->
					<view class="goods-price">￥{{goods_price}}</view>
					<!-- 商品数量 -->
					<uni-number-box :min="1"  :value="goods.goods_count" v-if="showNum" @change="numChangeHandler"></uni-number-box>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "my-goods",
		data() {
			return {
				defaultPic: 'https://img3.doubanio.com/f/movie/8dd0c794499fe925ae2ae89ee30cd225750457b4/pics/movie/celebrity-default-medium.png'
			};
		},
		props: {
			goods: {
				type: Object,
				defaul: {},
			},
			showRadio: {
				type: Boolean,
				defaul: false,
			},
			// 是否展示价格右侧的 NumberBox 组件
			showNum: {
			type: Boolean,
			default: false,
			},
		},
		computed: {
			'goods_price'() {
				return this.goods.goods_price.toFixed(2)

			}
		},
		methods: {
			radioClickHandler() {
				this.$emit('radio-change', {
					// 商品的 Id
					goods_id: this.goods.goods_id,
					// 商品最新的勾选状态
					goods_state: !this.goods.goods_state
				})

			},
			numChangeHandler(val){
				this.$emit('num-change',{
					// 商品的 Id
					goods_id: this.goods.goods_id,
					// 商品最新的勾选状态
					goods_count: +val
				})
			}
		}
	}
</script>

<style lang="scss">
	.goods-item {
		display: flex;
		padding: 10px 5px;
		border-bottom: 1px solid #f0f0f0;

		.goods-item-left {
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-right: 5px;

			.goods-pic {
				width: 100px;
				height: 100px;
				display: block;
			}
		}

		.goods-item-right {
			display: flex;
			flex: 1;
			flex-direction: column;
			justify-content: space-between;

			.goods-name {
				font-size: 13px;
			}
			.goods-info-box {
				display: flex;
				align-items: center;
				justify-content: space-between;
			}
			.goods-price {
				font-size: 16px;
				color: #c00000;
			}
		}
	}
</style>
