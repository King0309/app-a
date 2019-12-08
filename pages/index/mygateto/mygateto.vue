<template>
	<view>
		<text class="ddf">{{title}}</text>
		<p>{{meassge}}</p>
		<input class="content1" v-model="meassge" />
	</view>
</template>

<script>
	export default {
		onLoad:function(option){
			console.info("在我这个页面" + option.id);
		},
		data() {
			return {
				title: '测试跳转',
				meassge: 'hello'
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	
	page {
		color: #DD524D;
	}
	
	.ddf{
		display: flex;
		/* position: fixed; */
	}
	
	.content1{
		color: #4CD964;
		font-size: 15px;
		font: 300;
	}
	
	

</style>
