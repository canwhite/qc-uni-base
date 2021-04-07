<template>
	<view class="content">
		<cu-custom class="my_bg" :isBack="true">
			<!--<block slot="backText">返回</block> -->
			<block slot="content">base</block>
			<block slot="right">
				<view class="action">
					<!-- <view class="cu-load load-cuIcon" :class="!isLoad?'loading':'over'"></view> -->
				</view> 
			</block> 
		</cu-custom> 
	</view>
</template>

<script>
	// import {mapState} from 'vuex';
	export default {
		data() {
			return {
				title: 'Hello',
				page: 'index',
				showPage: false,
				containerHeight: 0,
			}
		},
		computed: {
			// ...mapState({
			// 	themeColor: 'themeColor',
			// 	tabbarTextColor: "tabbarTextColor",
			// 	tabbarTextActiveColor: "tabbarTextActiveColor",
			// })
		},
		
		methods:{

					
		},
		onLoad() {
			
		},
	
		onReady() {
			
			
			//跨域问题，简单解决办法就是用HBuilder内置浏览器运行
			(async ()=>{
				
				let res = await this.$request.get({
						url:"/weather",
	                    data:{
	                        city:"北京"
	                    },
				})
				console.log('------',res);
				
			})()
		},


	}
</script>

<style lang="scss">
	.my_bg{
		//渐进色的变化
		background-image: linear-gradient(45deg, #ff9700, #ed1c24);
		color: #ffffff;
	}
</style>
