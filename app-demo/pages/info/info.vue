<template>
	<view class="content">
		<view class="title">
			{{title}}
		</view>
		<view class="art-content">
			<rich-text class="rich-text" :nodes="strings"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				strings:''
			}
		},
		methods: {
			
		},
		onLoad(e) {
			//console.log(e);
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/' + e.newsid,
				method: 'GET',
				data: {},
				success: res => {
					console.log(res);
					this.title = res.data.title;	// res.data.title的存储位置赋值给this.title
					this.strings = res.data.content;	
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>
.content{
	padding: 10upx 2% ;	/*上下10upx,左右2%,*/
	width: 96%;
	flex-wrap: wrap;/*允许它下面的元素换行*/
}
.title{
	line-height: 2em;
	font-weight: 700;
	font-size: 38upx;
}
.art-content{
	line-height: 2em;
}
</style>
