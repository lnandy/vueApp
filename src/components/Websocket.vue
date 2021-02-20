<template>
	<div class="websocket_container">
		<div class="container">
			<h5>
				info:
			</h5>
			<div v-html="info.join('<br>')"></div>
		</div>
		<div class="send_info">
			<textarea rows="3" v-model="msg"></textarea>
			<button @click="websocketsend(msg)">send</button>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'websocket',
		data() {
			return {
				websock: null,
				info: [],
				msg: "",
			}
		},
		created() {
			this.initWebSocket();
		},
		destroyed() {
			this.websock.close() //离开路由之后断开websocket连接
		},
		methods: {
			initWebSocket() { //初始化weosocket
				const wsuri = "ws://192.168.0.104:3000";
				this.websock = new WebSocket(wsuri);
				this.websock.onmessage = this.websocketonmessage;
				this.websock.onopen = this.websocketonopen;
				this.websock.onerror = this.websocketonerror;
				this.websock.onclose = this.websocketclose;
				this.info.push('初始化weosocket');
			},
			websocketonopen() { //连接建立之后执行send方法发送数据
				// let actions = {
				// 	"test": "12345"
				// };
				this.websocketsend('weosocket已连接');
			},
			websocketonerror() { //连接建立失败重连
				this.initWebSocket();
			},
			websocketonmessage(e) { //数据接收
				//const redata = JSON.parse(e.data);
				this.info.push(e.data);
			},
			websocketsend(data) { //数据发送
				this.websock.send(data);
				this.msg = "";
			},
			websocketclose(e) { //关闭
				console.log('断开连接', e);
			},
		},
	}
</script>
<style lang='scss'>
	.websocket_container {
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;

		.container {
			display: flex;
			flex-direction: row;
			width: 100%;
			flex: 1;
		}

		h5 {
			margin: 5px 50px;
		}

		.send_info {
			width: 100%;
			display: flex;
			justify-content: center;

			textarea {
				width: 70%;
				resize: none;
			}
		}
	}
</style>
