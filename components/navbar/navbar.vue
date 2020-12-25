<template>
	<!-- 自定义导航栏  动态占位的高度 -->
	<view class="navbar" :style="{height: statusBarHeight+navBarHeight+'px'}">

		<view class="navbar-fixed">
			<!-- 状态栏 -->
			<view :style="{height: statusBarHeight +'px'}"></view>
			<!-- 导航栏内容 -->
			<view class="navbar-content" :style="{height:navBarHeight +'px', width:windowWidth+'px'}">
				<view class="navbar-search">
					<view class="navbar-search_icon">
						<!-- 使用插件显示 搜索按钮 -->
						<uni-icons type="search" size="16px" color="#999"></uni-icons>
					</view>
					<view class="navbar-search_text">uni-app、vue</view>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				statusBarHeight: 20,
				navBarHeight: 45,
				windowWidth: 375
			};
		},

		//组件加载会执行
		created() {
			//h5 app mmp-alipay
			//#ifndef H5||APP-PLUS||MP-ALIPAY
			//获取手机系统信息
			const info = uni.getSystemInfoSync()
			//设置状态栏高度 
			this.statusBarHeight = info.statusBarHeight
			this.windowWidth = info.windowWidth
			console.log(info);
			// 获取胶囊的位置
			const menuButtonInfo = uni.getMenuButtonBoundingClientRect()
			console.log(menuButtonInfo);
			// 导航栏高度=（胶囊底部高度-状态栏高度）+（胶囊顶部高度-状态栏内的高度）
			this.navBarHeight = (menuButtonInfo.bottom - info.statusBarHeight) + (menuButtonInfo.top - info.statusBarHeight)
			this.windowWidth = menuButtonInfo.left
			console.log(this.navBarHeight);
			// #endif
		}
	}
</script>

<style lang="scss">
	.navbar {
		.navbar-fixed {
			position: fixed;
			top: 0;
			left: 0;
			z-index: 99;
			width: 100%;
			background-color: $mk-base-color;

			.navbar-content {
				margin-top: 5px;
				display: flex;
				justify-content: center;
				align-items: center;
				height: 45px;
				padding: 15px;
				box-sizing: border-box; //盒内显示

				.navbar-search {
					display: flex;
					align-items: center;
					height: 30px;
					padding: 0 10px;
					width: 100%;
					
					/* #ifdef APP-PLUS */
					margin-right: 10px;
					/* #endif */
					border-radius: 30px;
					background-color: #fff;

					.navbar-search_icon {			
						margin-right: 10px;				
					}

					.navbar-search_text {
						font-size: 12px;
						color: #999;
					}
				}

			}

		}
	}
</style>
