<template>
	<view>
		<view>列表页</view>
		<view class="box-item" v-for="(item,index) in list" :key="index">
			{{item}}
		</view>
		<button @click="pullDown">下拉刷新</button>
	</view>
</template>




<script>
	export default{
		data() {
			return {
				list: ['前端','java','数据库','大数据','Payne','UI','测试','架构师','数据清洗','产品经理','项目经理']
			}
		},
		// 监听下拉刷新
		onPullDownRefresh(){
			console.log('触发下拉刷新')
			setTimeout(() => {
				this.list=  ['Payne','前端','java','数据库','大数据','组长','领导','人事部','行政部','政治部','财务部','老板']
				uni.stopPullDownRefresh() // 关闭下拉刷新
			}, 2000)
		},
		// 触底 刷新调用数据
		onReachBottom(){
			console.log('页面触底了')
			this.list = [...this.list,...['大润发','刘德华','周星驰','成龙','李连杰','洪金宝']]
		},
		
		methods: {
			pullDow(){
				uni.startPullDownRefresh()
			}
		}
	}
</script>

<style>
	.box-item{
		height: 100px;
		line-height: 100px;
	}
</style>
