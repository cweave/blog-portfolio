<template>
	<div class="home">
		<div class="overflow-container">
			<div class="star-container">
				<div class="star" v-for="(star, index) in stars" :key="index"></div>
			</div>
		</div>
		<div id="mountains"></div>
	</div>
</template>

<script>
	export default {
		name: 'home',
		data() {
			return {
				stars: 800
			};
		},
		mounted() {
			this.transformStar();
			document.getElementsByTagName('body')[0].setAttribute('id', 'home');
		},
		methods: {
			transformStar() {
				const stars = document.querySelectorAll('.star');
				stars.forEach((star) => {
					const s = 0.2 + (Math.random() * 1);
					const curR = this.stars + (Math.random() * 300);

					star.setAttribute('style', `transform-origin: 0 0 ${curR}px; transform: translate3d(0,0,-${curR}px) rotateY(${(Math.random() * 360)}deg) rotateX(${(Math.random() * -50)}deg) scale(${s}, ${s})`);
				});
			}
		}
	};
</script>

<style lang="scss">
	@keyframes rotate {
		0% { transform: perspective(600px) rotateZ(10deg) rotateX(-50deg) rotateY(0); }
		100% { transform: perspective(600px) rotateZ(10deg) rotateX(-50deg) rotateY(-360deg); }
	}

	.overflow-container {
		position: absolute;
		top: 0;
		width: 100%;
		height: 100vh;
		padding: 0;
		margin: 0;
		overflow: hidden;
	}

	.star-container {
		transform: perspective(800px);
		transform-style: preserve-3d;
		position: absolute;
		bottom: 0;
		perspective-origin: 50% 100%;
		left: 50%;
		animation: rotate 300s infinite linear;

		.star {
			width: 2px;
			height: 2px;
			background: #F7F7B6;
			position: absolute;
			top: 0;
			left: 0;
			transform-origin: 0 0 -300px;
			transform: translate3d(0,0,-300px);
			backface-visibility: hidden;
		}
	}

	#mountains {
		position: absolute;
		bottom: 0;
		width: 100%;
		height: 100vh;
		z-index: 1;
		background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1600 900'%3E%3Cpolygon fill='%231c6f92' points='957 450 539 900 1396 900'/%3E%3Cpolygon fill='%2329abe2' points='957 450 872.9 900 1396 900'/%3E%3Cpolygon fill='%23417592' points='-60 900 398 662 816 900'/%3E%3Cpolygon fill='%2367b7e2' points='337 900 398 662 816 900'/%3E%3Cpolygon fill='%235d8095' points='1203 546 1552 900 876 900'/%3E%3Cpolygon fill='%238ec3e5' points='1203 546 1552 900 1162 900'/%3E%3Cpolygon fill='%23718796' points='641 695 886 900 367 900'/%3E%3Cpolygon fill='%23accde3' points='587 900 641 695 886 900'/%3E%3Cpolygon fill='%23848f96' points='1710 900 1401 632 1096 900'/%3E%3Cpolygon fill='%23ccdce7' points='1710 900 1401 632 1365 900'/%3E%3Cpolygon fill='%23969696' points='1210 900 971 687 725 900'/%3E%3Cpolygon fill='%23e0e0e0' points='943 900 1210 900 971 687'/%3E%3C/svg%3E");
		background-size: cover
	}

</style>
