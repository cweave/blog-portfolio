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

<script>
	export default {
		watch: {
			$route: {
				handler(to, from) {
					const body = document.getElementsByTagName('body')[0];
					if (from !== 'home') {
						body.removeAttribute('id', 'home');
					}
				},
				immediate: true
			}
		}
	};
</script>

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

	body {
		margin: 0;
		font-size: 18px;
		line-height: 1.5;
		font-family: 'Fira', sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		color: $black-blue;
		background: linear-gradient(to bottom, rgba(4,13,48,1) 0%, rgba(27,41,71,1) 52%, rgba(56,61,149,1) 86%, rgb(56, 61, 149) 100%);;
		background-attachment: fixed;
		overflow: visible;
	}

#nav {
	padding: 30px;
	z-index: 3;
	position: relative;

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
