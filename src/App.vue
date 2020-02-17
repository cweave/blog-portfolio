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
	@import url('https://fonts.googleapis.com/css?family=Fira+Sans:400,400i,700,700i');
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

	#app {
		height: 100%;
	}

	#nav {
		padding: 30px;
		z-index: 3;
		position: relative;

		a {
			font-weight: bold;
			color: $black;

			&.router-link-exact-active {
				color: $mint;
			}
		}
	}

</style>
