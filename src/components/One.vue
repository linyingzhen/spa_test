<template>
	<div>
		<div>{{ msg }}</div>
		<div id="demo">
		  <button v-on:click="show = !show">
		    Toggle
		  </button>
		  <transition name="fade">
		    <p v-if="show">hello</p>
		  </transition>
		</div>
		<div id="example-1">
		  <button @click="show = !show">
		    Toggle render
		  </button>
		  <transition name="slide-fade">
		    <p v-if="show">hello</p>
		  </transition>
		</div>
		<div v-on:click="showdatamsg()">showdatamsg</div>
		<ul>
			<li v-for="method in methods" v-on:click="choiceresult(method)">{{method}}</li>
		</ul>
		<van-switch v-model="checked" />
		<van-radio name="1" v-model="radio">单选框 1</van-radio>
		<van-radio name="2" v-model="radio">单选框 2</van-radio>
		<van-row>
		  <van-col span="8">span: 8</van-col>
		  <van-col span="8">span: 8</van-col>
		  <van-col span="8">span: 8</van-col>
		</van-row>
		<van-row gutter="20">
		  <van-col span="8">span: 8</van-col>
		  <van-col span="8">span: 8</van-col>
		  <van-col span="8">span: 8</van-col>
		</van-row>
		<el-switch
		  v-model="value2"
		  active-color="#13ce66"
		  inactive-color="#ff4949">
		</el-switch>
		<div>
		  <el-button>默认按钮</el-button>
		  <el-button type="primary">主要按钮</el-button>
		  <el-button type="success">成功按钮</el-button>
		  <el-button type="info">信息按钮</el-button>
		  <el-button type="warning">警告按钮</el-button>
		  <el-button type="danger">危险按钮</el-button>
		</div>

		<div style="margin: 20px 0">
		  <el-button plain>朴素按钮</el-button>
		  <el-button type="primary" plain>主要按钮</el-button>
		  <el-button type="success" plain>成功按钮</el-button>
		  <el-button type="info" plain>信息按钮</el-button>
		  <el-button type="warning" plain>警告按钮</el-button>
		  <el-button type="danger" plain>危险按钮</el-button>
		</div>

		<div>
		  <el-button round>圆形按钮</el-button>
		  <el-button type="primary" round>主要按钮</el-button>
		  <el-button type="success" round>成功按钮</el-button>
		  <el-button type="info" round>信息按钮</el-button>
		  <el-button type="warning" round>警告按钮</el-button>
		  <el-button type="danger" round>危险按钮</el-button>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'One',
		props: {
			msg: String
		},
		data() {
			return {
				methods:[1,2,3],
				show: true,
				checked: true,
				radio: '1',
				value1: true,
				value2: true
			}
		},
		methods: {
			choiceresult:function(ss){
				this.choiced = ss;
				console.log(this.choiced);
			},
			showdatamsg:function(){
				this.$http.get('/static/data.json').then(response => {
				    // success callback
				    console.log(typeof(response.data));
				}, response => {
				    // error callback

				})
			}
		}
	}
</script>





<style scoped>

/* 可以设置不同的进入和离开动画 */
/* 设置持续时间和动画函数 */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

</style>