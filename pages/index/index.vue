<template>
	<view class="content">
		<button v-on:click="fes('dd')">fed</button>
		<button v-on:click="jsonRequest()">请求后台get</button>
		<button v-on:click="jsonPostRequest()">请求后台post</button>
		<view v-model="userdata" class="text-row">
			<text id="name">{{userdata.name}}</text>
			<text>{{userdata.age}}</text>
			<text>{{userdata.sex}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'ssd',
				userdata: ''
			}
		}, 
		onLoad() {
			console.info("onload()");
		},
		onShow() {
			console.info("onshow");
		},
		onReady() {
			console.info("onready");
		},
		onHide() {
			console.info("onhide");
		},
		onUnload() {
			console.info("onUnload");
		},
		onResize() {
			console.info("onResize");
		},
		methods: {
			
			fes(reccept){
				console.info("看看是不是这报错");
				uni.navigateTo({
					url: 'mygateto/mygateto?id=1',
					success: res => {
						console.info("跳转成功了");
					},
					fail: () => {
						console.error("跳转失败了");
					},
					complete: () => {
						console.info("跳转完成了");
					}
				});
			},
			
			jsonRequest(){
				console.info("准备请求后台服务");
				uni.request({
					url: 'http://localhost:9091/async/uni/data',
					method: 'GET',
					data: {
						name: 'gyy',
						age: 23,
						sex: 1
					},
					header: {
						'costom-header': 'hello',
						'content-type': 'application/json',
						'Access-Control-Allow-Origin': '*'
					},
					success: (res) => {
						console.info("res.data = " + res.data);
					}
				})
			},
			
			jsonPostRequest(){
				console.info("准备发起post请求的");
				uni.request({
					url: 'http://localhost:9091/async/uni/post/data',
					method: 'POST',
					data: {
						name: 'gyy',
						age: 23,
						sex: 1
					},
					header: {
						'costom-header': 'hello',
						'content-type': 'application/json',
					},
					dataType: 'json',
					success: (res) => {
						console.info(res.data);
						this.userdata = res.data;
					},
					fail: (data) => {
						console.info(res.data);
					}
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: margin-left;
		justify-content: margin-left;
	}
	
	
	.text-row{
		display: inline-flex;
		flex-direction: row;
		justify-content: space-between;
		align-content: center;
		background: #FFFFFF;
		padding:20px;
		border-bottom:#EFEFF4 solid 2px;
		color: #1296db;
		outline: #333333;
		outline-style: auto;
		outline-width: initial;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}


	.title {
		font-size: 72rpx;
		color: #8f8f94;
	}
</style>
