<template>
	<div id="app">
		<div id="nav">
			<router-link to="/">Home</router-link> |
			<router-link to="/blog">Blog</router-link>
		</div>
		<transition name="fade" mode="out-in">
			<router-view></router-view>
		</transition>
	</div>
</template>

<style lang="scss">
	.fade-enter-active,
	.fade-leave-active {
		transition-duration: 0.2s;
		transition-property: opacity;
		transition-timing-function: ease;
	}

	.fade-enter,
	.fade-leave-active {
		opacity: 0
	}

	html,
	body {
		height: 100%;
		margin: 0;
		font-size: 18px;
		line-height: 1.5;
		font-family: 'Fira', sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		color: $black-blue;
		background: #040d30;
		background: linear-gradient(to bottom,  #040d30 0%,#1b2947 52%,#383d95 86%,#383d95 100%) no-repeat center center fixed;
		@media #{$mobile-devices} {
			position: relative;
		}

		// background-attachment: fixed mobile hack
		@media #{$mobile-devices} {
			&:before {
				content: ' ';
				position: fixed;
				width: 100%;
				height: 100%;
				top: 0;
				left: 0;
				background: -moz-linear-gradient(top,  #040d30 0%, #1b2947 52%, #383d95 86%, #383d95 100%); // FF3.6-15
				background: -webkit-linear-gradient(top,  #040d30 0%,#1b2947 52%,#383d95 86%,#383d95 100%); // Chrome10-25,Safari5.1-6
				background: linear-gradient(to bottom,  #040d30 0%,#1b2947 52%,#383d95 86%,#383d95 100%) no-repeat center center fixed; // W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+
				background-size: cover;
				will-change: transform;
				// creates a new paint layer
				backface-visibility: hidden;
				-webkit-backface-visibility: hidden;
				z-index: -1;
			}
		}
	}

	#app {
		height: 100%;
	}

#nav {
	padding: 30px;
	z-index: 3;
	position: absolute;

	a {
		font-weight: bold;
		color: $black-blue;

		&.router-link-exact-active {
			color: $mint;
		}
	}
}

a {
	text-decoration: none;
	color: $black-blue;
	background-image: linear-gradient(120deg, $mint 0%, $skyblue 100%);
	background-repeat: no-repeat;
	background-size: 100% 0.25em;
	background-position: 0 95%;
	transition: background-size 0.25s ease-in;

	&:hover {
		background-size: 100% 90%;
		cursor: pointer;
		text-shadow: 0 1px 2px rgba($white, 0.2);
	}
}
</style>
