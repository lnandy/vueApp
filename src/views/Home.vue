<template>
  <div class="home_container">
    <router-link to="/scan">扫一扫</router-link>
	<button @click="test">是否有延迟</button>
	<Websocket></Websocket>
  </div>
</template>

<script>
	// @ is an alias to /src
	import Websocket from '@/components/Websocket.vue'
	export default {
		name: 'home',
		components: {
			Websocket: Websocket
		},
		methods:{
			test(){
				alert(0);
			}
		}
	}
</script>
<style lang="less">
	.home_container{
		width: 100%;
		height: 100%;
		.websocket_container{
			height: 95%;
		}
	}
</style>
