<template>
	<div class="scan_container">
		<!-- <input type='button' @click='startRecognize' value='创建扫描控件' />
		<input type='button' @click='startScan' value='开始扫描' />
		<input type='button' @click='cancelScan' value='取消扫描' /> -->
		<input type='button' @click='setFlash' value='开启闪光灯' />
		<input type='button' @click='goback' value='返回' />
		<div id="bcid"></div>
	</div>
</template>

<script>
	export default {
		name: 'Scan',
		mounted() {
			let me = this;
			// document.addEventListener( "plusready", onPlusReady, false );
			// // 扩展API加载完毕，现在可以正常调用扩展API
			// function onPlusReady() {
			//     // var e = document.getElementById("scan");
			//     // e.removeAttribute( "disabled" );
			// 	me.startRecognize();
			// 	alert('okokokok');
			// }
			// scan = null;
			setTimeout(function() {
				me.startRecognize();
			}, 0)
		},
		destroyed() {
			if (!window.plus) return;
			scan.close();
			scan = undefined;
		},
		// 创建扫描控件
		methods: {
			goback() {
				this.$router.go(-1);
			},
			onmarked(type, result) {
				let me = this;
				var text = '未知: ';
				switch (type) {
					case plus.barcode.QR:
						text = 'QR: ';
						break;
					case plus.barcode.EAN13:
						text = 'EAN13: ';
						break;
					case plus.barcode.EAN8:
						text = 'EAN8: ';
						break;
				}
				alert(text + result);
				me.goback();
			},
			startRecognize() {
				let me = this;
				scan = new plus.barcode.Barcode('bcid');
				scan.onmarked = me.onmarked;
				me.startScan();
			},
			startScan() {
				scan.start();
			},
			cancelScan() {
				scan.cancel();
			},
			setFlash() {
				scan.setFlash();
			}
		}
	}
</script>
<style scoped lang="less">
	.scan_container{
		width: 100%;
		height: 100%;
	}
	#bcid {
		background: #0F0;
		height: 100%;
		width: 100%;
	}
	input[type="button"]{
		float: left;
	}
</style>
