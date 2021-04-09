<template>
	<view >
		<cu-custom bgColor="bg-white"  :isBack="true">
<!-- 			<block slot="backText">返回</block> -->
			<block slot="content">base</block>
			<block slot="right">
				<view class="action">
					<!-- <view class="cu-load load-cuIcon" :class="!isLoad?'loading':'over'"></view> -->
				</view> 
			</block> 
		</cu-custom> 
		<scroll-view scroll-y="true" class="app-container" :style="'height:'+containerHeight+'px'">
			<view> 我是正文</view>
		</scroll-view>




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
			async init_page_size() {
				console.log("init_page_size")
				this.$nextTick(async () => {
					let sysInfo = uni.getSystemInfoSync();
					//uni-app获取element
					/*
					const query = uni.createSelectorQuery().in(this);
					const tabbarObj = query.select('#tabbar')
					let tabbarNodeRes = await this.syncBoundingClientRect(tabbarObj);
					
					*/
					//如果没有navbar这里就不用减了
					let pageHeight = sysInfo.windowHeight - this.CustomBar;
					this.containerHeight = pageHeight;
					this.showPage = true;
				})
			},	

					
		},
		onLoad() {
			
		},
	
		onReady() {
			
			this.init_page_size();
			
			
			//跨域问题，简单解决办法就是用HBuilder内置浏览器运行
			/*
				(async ()=>{
					
					let res = await this.$request.get({
							url:"/weather",
		                     data:{
		                         city:"北京"
		                     },
					})
					console.log('------',res);
					
				})()
				
				*/
				
			},

		

	}
</script>

<style lang="scss">
	
	
	.my_bg{
		background-color: #FFFFFF;
	}	

	.app-container {
		min-height: 600upx;
		background-color: white;
	}
	
</style>
