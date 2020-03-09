<template>
	<div class="home">
		<!-- <div class="overflow-container">
			<div class="star-container">
				<div class="star" v-for="(star, index) in stars" :key="index"></div>
			</div>
		</div> -->

		<div id="mountains"></div>
		<div class="moon"></div>
		<div class="welcome">
			christa weaver
		</div>


		<div class="personal-information__grid-container grid-container">
			<div class="about">
				<h2 class="gradient-text">Priestess of software, goddess of code.</h2>
				<p>My passion for web development started around the age of 11 with Invisionfree forums and learning what CSS was and how to create different skins. Then the discovery of MySpace happened, and it was all downhill from there (well, maybe not downhill, since my obsession eventually landed me into a career).</p>
				<p>Currently, I am a front-end engineer at Cognito Forms located in Columbia, South Carolina (but my roots are from Michigan). I have extensive experience with sematic HTML, SCSS, and vanilla JavaScript (ES6+). My current pathway is aligned with JavaScript development, with a current focus in VueJs. Vue test utils and Jest are also in my JavaScript arsenal, ya know, to make sure everything is working smoothly.</p>
				<p>By daylight, I click away at my rainbow backlight mechanical keyboard. In my spare time, I am a reader of sci-fi and mystery books, an enjoyer of psychological thrillers, and have a newfound enjoyment with playing Dungeons & Dragons.</p>
				<span>¯\(ツ)/¯ and (╯°□°）╯︵ ┻━┻ are my two natural states</span>
			</div>
			<div class="history">
				<JobHistory />
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
	.home {
		position: absolute;
		top: 0;
	}
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
		@include mountains;
	}

	.moon {
		position: absolute;
		top: 1em;
		right: 1em;
		background: url(https://raw.githubusercontent.com/yagoestevez/fcc-portfolio/master/src/Images/Moon.svg?sanitize=true) right 100% no-repeat;
		background-size: 40% 40%;
		width: 50%;
		height: 50%;
		z-index: 1;
		animation: moon-move-in 1.2s 1s forwards;
	}

	@keyframes moon-move-in {
		from {
			opacity: 0;
			background-position: right 150%;
		}
		to {
			opacity: 1;
			background-position: top right;
		}
	}

	.welcome {
		width: fit-content;
		position: absolute;
		right: 0;
		top: 15%;
		left: 25%;
		opacity: 0;
		transform: translate(0, -15%);
		animation: text-fade-in 1000ms 800ms forwards;
	}

	@keyframes text-fade-in {
		from {
			right: 0;
		}
		to {
			opacity: 1;
			right: 25%;
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

	.personal-information {

		&__grid-container {
			padding: 1.25em;

			& > div:nth-child(1)  { grid-area: about; }
			& > div:nth-child(2)  { grid-area: history; }

			& {
				grid-template-areas:
					"about about"
					"history history";

				@media screen and (min-width: 750px) {
					grid-template-areas:
					"about history";
				}
			}
		}
	}
</style>
