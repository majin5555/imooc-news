<template>

	<view class="scroll">
		<scroll-view class="list-srcoll" scroll-y>
			<view>
				<slot></slot>
			</view>
		</scroll-view>

	</view>

</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.scroll {
		flex: 1;
		overflow: hidden;
		box-sizing: border-box;

		.list-srcoll {
			height: 100%;
			display: flex;
			flex-direction: column;
		}
	}
</style>
