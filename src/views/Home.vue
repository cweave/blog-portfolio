<template>
	<div class="home">
		<div class="overflow-container">
			<div class="star-container">
				<div class="star" v-for="(star, index) in stars" :key="index"></div>
			</div>
		</div>

		<div id="mountains"></div>


		<div class="grid">
			<div class="item">
				<div class="box">
					<h2 class="gradient-text">Priestess of software, goddess of code.</h2>
					<p>My passion for web development started around the age of 11 with Invisionfree forums and learning what CSS was and how to create different skins. Then the discovery of MySpace happened, and it was all downhill from there (well, maybe not downhill, since my obsession eventually landed me into a career).</p>
					<p>Currently, I am a front-end engineer at Cognito Forms located in Columbia, South Carolina (but my roots are from Michigan). I have extensive experience with sematic HTML, SCSS, and vanilla JavaScript (ES6+). My current pathway is aligned with JavaScript development, with a current focus in VueJs. Vue test utils and Jest are also in my JavaScript arsenal, ya know, to make sure everything is working smoothly.</p>
					<p>By daylight, I click away at my rainbow backlight mechanical keyboard. In my spare time, I am a reader of sci-fi and mystery books, an enjoyer of psychological thrillers, and have a newfound enjoyment with playing Dungeons & Dragons.</p>
					<span>¯\(ツ)/¯ and (╯°□°）╯︵ ┻━┻ are my two natural states</span>
				</div>
			</div>
			<div class="item">
				<div class="box">
					<JobHistory />
				</div>
			</div>

		</div>
	</div>
</template>

<script>
	import JobHistory from '@/components/JobHistory.vue';

	export default {
		name: 'home',
		components: {
			JobHistory
		},
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
		position: relative;
		bottom: 0;
		width: 100%;
		height: 100vh;
		z-index: 1;
		background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1600 900'%3E%3Cpolygon fill='%231c6f92' points='957 450 539 900 1396 900'/%3E%3Cpolygon fill='%2329abe2' points='957 450 872.9 900 1396 900'/%3E%3Cpolygon fill='%23417592' points='-60 900 398 662 816 900'/%3E%3Cpolygon fill='%2367b7e2' points='337 900 398 662 816 900'/%3E%3Cpolygon fill='%235d8095' points='1203 546 1552 900 876 900'/%3E%3Cpolygon fill='%238ec3e5' points='1203 546 1552 900 1162 900'/%3E%3Cpolygon fill='%23718796' points='641 695 886 900 367 900'/%3E%3Cpolygon fill='%23accde3' points='587 900 641 695 886 900'/%3E%3Cpolygon fill='%23848f96' points='1710 900 1401 632 1096 900'/%3E%3Cpolygon fill='%23ccdce7' points='1710 900 1401 632 1365 900'/%3E%3Cpolygon fill='%23969696' points='1210 900 971 687 725 900'/%3E%3Cpolygon fill='%23e0e0e0' points='943 900 1210 900 971 687'/%3E%3C/svg%3E") no-repeat center bottom;
		background-size: cover;

		@media #{$mobile-devices} {
			bottom: unset;
		}
	}

	.gradient-text {
		font-size: 4rem;
		line-height: 0.9;
		text-transform: uppercase;
		background: linear-gradient(to right, $skyblue 0%, #1b2947 100%);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		margin: 0;
	}

	@supports (display: grid) {

	.grid {
		display: grid;
		grid-gap: 1vw;
		padding: 2vw;
	}

	.grid {
		grid-template-columns: 1fr;
		grid-template-rows: auto;
		grid-template-areas:
			"hero   hero"
			"hero2   hero2";
	}

	@media screen and (min-width: 750px) {
		.grid {
			grid-template-columns: repeat(5, 1fr);
			grid-template-areas:
				"hero   hero   hero   hero2   hero2"
				"hero   hero   hero   hero2   hero2"
				"hero   hero   hero   hero2   hero2";
		}
	}

	@media screen and (min-width: 1400px) {
		.grid {
			grid-template-columns: repeat(5, 1fr);
			grid-template-areas:
				"hero	hero	hero	hero2	hero2"
				"hero	hero	hero	hero2	hero2"
				"hero	hero	hero	hero2	hero2";
		}
	}

	.grid .item:nth-child(1)  { grid-area: hero; }
	.grid .item:nth-child(2)  { grid-area: hero2; }
}


/* flexbox fallback is the browser does not support display:grid */
@supports not (display: grid) {

	.grid {
		display: flex;
		flex-flow: row wrap;
		min-height: 100vh;
		padding: 0.75vw;
	}

	.grid .item {
		min-height: 20vh;
		margin: 0.75vw;
	}

	.grid .item:nth-child(1)  { flex: 0 1 calc(100% - 1.5vw); height: 50vh; }
	.grid .item:nth-child(2)  { flex: 0 1 calc(100% - 1.5vw); }
	.grid .item:nth-child(3)  { flex: 0 1 calc(100% - 1.5vw); }

	@media screen and (min-width: 750px) {
		.grid .item:nth-child(1)  { flex: 0 1 calc(60% - 1.5vw); }
		.grid .item:nth-child(2)  { flex: 0 1 calc(40% - 1.5vw); height: 50vh; }
	}

	@media screen and (min-width: 1400px) {
		.grid .item:nth-child(1)  { flex: 0 1 calc(60% - 1.5vw); }
		.grid .item:nth-child(2)  { flex: 0 1 calc(40% - 1.5vw); }
		.grid .item:nth-child(3)  { flex: 0 1 calc(50% - 1.5vw); }
	}

}

/* Styles, just for fun */

.box {
	height: 100%;
}

.grid .item {
	padding: 1vw;
	background-color: $white;
	border-radius: 0.5em;
	box-shadow: 0 5px 20px rgba($white, 0.12);
}

</style>
