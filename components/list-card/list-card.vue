<template>
	<view>
		<!-- 基础卡片 -->
		<view v-if="mode==='base'" class="listcard">
			<view class="listcard-image">
				<image src="../../static/logo.png" mode="aspectFill"></image>
			</view>
			<view class="listcard-content">
				<view class="listcard-content_title">
					<text>
						uni-app 开发框架uni-app 开发框架uni-app 开发框架uni-app 开发框架uni-app 开发框架
					</text>
				</view>
				<view class="listcard-content_des">
					<view class="list-card_des_label">
						<view class="list-card_des_label_item">前端</view>
					</view>
					<view class="list-card_des_browse">360浏览</view>
				</view>
			</view>
		</view>


		<!-- 多图模式 -->
		<view  v-if="mode==='column'" class="listcard mode-column">
			<view class="listcard-content">
				<view class="listcard-content_title">
					<text>
						uni-app 开发框架uni-app 开发框架uni-app 开发框架uni-app 开发框架uni-app 开发框架
					</text>

				</view>
				<view class="listcard-image">
					<view v-for="item in 3" :key="item" class="listcard-image_item">
						<image src="../../static/logo.png" mode="aspectFill"></image>
					</view>
				</view>
				<view class="listcard-content_des">
					<view class="list-card_des_label">
						<view class="list-card_des_label_item">前端</view>
					</view>
					<view class="list-card_des_browse">360浏览</view>
				</view>
			</view>
		</view>

		<!-- 大图模式 -->
		<view v-if="mode==='image'"  class="listcard mode-image">
			<view class="listcard-image">
				<image src="../../static/logo.png" mode="aspectFill"></image>
			</view>
			<view class="listcard-content">

				<view class="listcard-content_title">
					<text>
						uni-app 开发框架uni-app 开发框架uni-app 开发框架uni-app 开发框架uni-app 开发框架
					</text>

				</view>

				<view class="listcard-content_des">
					<view class="list-card_des_label">
						<view class="list-card_des_label_item">前端</view>
					</view>
					<view class="list-card_des_browse">360浏览</view>
				</view>
			</view>
		</view>


	</view>
</template>

<script>
	export default {
		props: {
			mode: {
				type: String,
				default: 'base'
			}
		},
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.listcard {
		display: flex;
		padding: 10px;
		margin: 10px;
		border-radius: 5px;
		box-shadow: 0 0 5px 1px rgba($color: #000000, $alpha: 0.1);
		box-sizing: border-box;

		.listcard-image {
			height: 60px;
			flex-shrink: 0;
			width: 60px;
			border-radius: 5px;
			overflow: hidden;

			image {
				width: 100%;
				height: 100%;
			}
		}

		.listcard-content {
			display: flex;
			justify-content: space-between;
			flex-direction: column;
			padding-left: 10px;
			width: 100%;

			.listcard-content_title {
				font-size: 14px;
				color: #333;
				font-weight: 400;
				line-height: 1.2;

				text {
					/* 文字一处隐藏 */
					overflow: hidden;
					text-overflow: ellipsis;
					display: -webkit-box;
					-webkit-line-clamp: 2;
					-webkit-box-orient: vertical;
				}
			}

			.listcard-content_des {
				display: flex;
				justify-content: space-between;
				font-size: 12px;

				.list-card_des_label {
					display: flex;

					.list-card_des_label_item {
						color: $mk-base-color;
						padding: 0 5px;
						margin-right: 5px;
						border-radius: 3px;
						border: 1px $mk-base-color solid;
					}
				}

				.list-card_des_browse {
					color: #999;
					line-height: 1.5;
				}
			}
		}

		&.mode-column {

			.listcard-content {

				width: 100%;
				padding-left: 0;

				.listcard-image {
					display: flex;
					margin-top: 10px;
					width: 100%;
					height: 70px;

					.listcard-image_item {
						margin-left: 10px;
						width: 100%;
						border-radius: 5px;
						overflow: hidden;

						&:first-child {
							margin-left: 0;
						}

						image {
							width: 100%;
							height: 100%;

						}
					}

				}

				.listcard-content_des {
					margin-top: 10px;
				}
			}
		}

		&.mode-image {
			flex-direction: column;

			.listcard-image {
				width: 100%;
				height: 100px;
			}

			.listcard-content {
				padding-left: 0;
				margin-top: 10px;

				.listcard-content_des {
					display: flex;
					align-items: center;
					margin-top: 10px;
				}
			}
		}
	}
</style>
