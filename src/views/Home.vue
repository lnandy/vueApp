<template>
  <div class="content">
    <router-link to="/scan">扫一扫</router-link>
	<button @click="test">是否有延迟</button>
  </div>
</template>

<script>
	// @ is an alias to /src
	export default {
		name: 'home',
		components: {
		},
		methods:{
			test(){
				alert(0);
			}
		}
	}
</script>
<style scoped lang="less">
	.content {
		background-color: #000;
		color: white;
		height: 100vh;
		overflow: hidden;

		header {
			background-color: #000;
			height: 2.00533rem;
			width: 100%;
			text-align: center;
			line-height: 2.00533rem;
			display: flex;
			/*position: fixed;*/
			top: 0;
			z-index: 99999;

			/deep/ .head_goback {
				padding-top: 0.1rem;
				width: 0.6rem;
				height: 0.8533rem;
				padding-left: 0.2rem;
			}

			/deep/ .title_head {
				width: 92%;
				text-align: center;
				color: white;
				font-size: 0.8533rem;
				letter-spacing: 2px;
			}
		}

		.Detail {
			width: 96%;
			margin: 0 auto;

			.session {
				.name {
					margin: 0.4rem 0;
					font-size: 0.4rem;
					color: #333333;
					font-weight: bold;
				}

				.useTutorials {
					background-color: #3998F7;
					border-radius: 5px;
				}

				.desc {
					margin: 0.4rem 0;
					font-size: 0.4rem;
					color: #333333;

					.title {
						font-weight: bold;
					}

					.intro {
						margin-top: 0.1rem;
					}
				}
			}

			p {
				font-size: 0.72rem;
			}

			.sweep {
				text-align: center;
				margin: 0.1rem auto;
				width: 13.8667rem;
				height: 1.7067rem;
				display: flex;
				justify-content: center;
				align-items: center;
				border-radius: 1.024rem;
				font-size: 0.768rem;
				position: relative;
				z-index: 9999;
				color: white;
				background: #FF8C99;
				box-shadow: 0px 6px 9px 0px rgba(255, 140, 153, 0.57);
				margin-top: 2rem;
			}
		}

		.start {
			text-align: center;
			margin: 0 auto;
			width: 13.8667rem;
			height: 1.7067rem;
			display: flex;
			justify-content: center;
			align-items: center;
			border-radius: 1.024rem;
			font-size: 0.768rem;
			background: white;
			border: 2px solid rgba(255, 169, 163, 1);
			color: rgba(255, 169, 163, 1);
			margin-top: 0.64rem;
		}
	}
</style>
