<template>
	<div class="blog-post">
		<router-view />
		<button @click="$router.go(-1)">&laquo; Back</button>
	</div>
</template>

<style lang="scss" scopped>
	.blog-post {
		width: 70vw;
		margin: 0 auto;
		background-color: white;
		padding: 2em;
		border-radius: .5rem;
		position: relative;
		z-index: 2;

		pre {
			background-color: #455a64;
			padding: 1rem;
			border-radius: .5rem;
			box-shadow: 0 5px 20px rgba($black, .2);
			text-align: left;
			width: 55vw;
			margin: 2.25em auto;
			white-space: pre-wrap;
			word-break: break-word;

			code {
				color: white;
				font-size: 1.1em;
				line-height: 1;

				&.language-js {
					.hljs {
						&-comment {
							color: #999999;
						}

						&-keyword {
							color: #29ABE2;
							font-weight: bold;
							font-style: italic;
						}

						&-string {
							color: palegoldenrod;
						}

						&-attr {
							color: paleturquoise;
						}

						&-number {
							color: palevioletred;
						}
					}
				}
			}
		}

		h1,
		h2,
		h3,
		h4,
		h5,
		p {
			code {
				background-color: lighten(#455a64, 60%);
				padding: 0.25em;
				border-radius: 0.25em;
				white-space: pre-wrap;
				word-break: break-word;
			}
		}
	}
</style>
