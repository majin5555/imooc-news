<template>
	<view class="home">
		<!--自定义导航栏组件 -->
		<navbar></navbar>
		<tab :list='tabList' @tab="tab"></tab>
		<view class="home-list">
			<list></list>
		</view>
	</view>
</template>

<script>
	//easyCom components/组件名/组件名.vue 可以直接使用 局部引入 不需要import
	//引入navbar组件
	//import navbar from '@/components/navbar/navbar.vue'

	export default {
		data() {
			return {
				title: 'Hello',
				tabList: [],
			}
		},
		onLoad() {
			this.getLabel()
			console.log("index onLoad()");
		},
		onShow() {
			console.log("index onShow()");

		},
		methods: {
			//选项卡点击事件
			tab({
				data,
				index
			}) {
				console.log("选项卡item点击事件 " + data, index);
			},
			//获取云函数
			getLabel() {
				//console.log(this.$api);
				this.$api.get_label({
					name: 'get_label'
				}).then((res => {
					const {
						data
					} = res
					this.tabList = data
					//console.log(res);
				}))
			},
		}
	}
</script>
<!-- 样式用scss开发 -->
<style lang="scss">
	page {
		height: 100%;
		display: flex;
	}

	.home {
		display: flex;
		flex-direction: column;
		flex: 1;
		border: 1px green solid;
		overflow: hidden;

		.home-list {
			flex: 1;
			box-sizing: border-box;
			
		}
	}
</style>
