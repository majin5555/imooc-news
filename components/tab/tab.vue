<template>
	<view class="tab">
		<scroll-view class="tab-scroll" scroll-x>
			<view class="tab-scroll_box">
				<view v-for="(item, index) in list" :key="index" class="tab-scoll_item" :class="{active:activeIndex === index}" @click="clickTab(item, index)">{{item.name}}
				</view>
			</view>
		</scroll-view>
		<view class="tab-icons">
			<uni-icons type="gear" size="26px" color="#666"></uni-icons>
		</view>
	</view>
</template>

<script>
	export default {
		//与外部通信传值
		props: {
			list: {
				type: Array,
				default () {
					return []
				}
			}
		},
		data() {
			return {
				activeIndex: 0 
			};
		},
		methods: {
			clickTab(item, index) {  
				// console.log(item, index);
				this.activeIndex = index
				//事件的发送
				this.$emit('tab', { 
					data: item,
					index: index
				})
			}
		}
	}
</script>

<style lang="scss">
	.tab {
		display: flex;
		background-color: #fff;
		border-bottom: 1px #f5f5f5 solid;
		width: 100%;
		box-sizing: border-box;

		.tab-scroll {
			flex: 1; //tab 撑满整个元素
			overflow: hidden; //溢出隐藏
			box-sizing: border-box;

			.tab-scroll_box {
				display: flex;
				height: 45px;
				align-items: center;
				flex-wrap: nowrap;
				box-sizing: border-box;

				.tab-scoll_item {
					flex-shrink: 0; //不让元素挤压
					padding: 0 10px;
					color: 14px;
					size: 14px;

					&.active {
						color: $mk-base-color;
					}
				}
			}

		}

		.tab-icons {
			position: relative;
			display: flex;
			justify-content: center;
			align-items: center;
			width: 45rpx;

			&::after {
				content: '';
				position: absolute;
				top: 12px;
				bottom: 12px;
				left: 0;
				width: 1px;
				background-color: #ddd;
			}
		}
	}
</style>
