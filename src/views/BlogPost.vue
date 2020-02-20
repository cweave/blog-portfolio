<template>
	<div class="content">
		<router-view />
		<button class="btn btn--primary" @click="$router.go(-1)">&laquo; Back</button>
	</div>
</template>

<script>
	import prism from '@/scripts/prism';

	export default {
		mounted() {
			prism();
		}
	};
</script>

<style lang="scss" scopped>

	section {
		width: 70vw;
		background-color: white;
		padding: 2em;
		border-radius: .5rem;
	}

	pre,
	code,
	pre code[class*="language-"] {
		color: $white;
		background: none;
		font-family: Consolas, Monaco, 'Andale Mono', 'Ubuntu Mono', monospace;
		font-size: 1em;
		text-align: left;
		white-space: pre;
		word-spacing: normal;
		word-break: normal;
		word-wrap: normal;
		line-height: 1.5;

		-moz-tab-size: 4;
		-o-tab-size: 4;
		tab-size: 4;

		-webkit-hyphens: none;
		-moz-hyphens: none;
		-ms-hyphens: none;
		hyphens: none;

	}
	/* Code blocks */
	pre[class*="language-"] {
		padding: 1em;
		margin: .5em 0;
		overflow: auto;
	}

	:not(pre) > code[class*="language-"],
	pre {
		background-color: #455a64;
		padding: 1rem;
		border-radius: .5rem;
	}

	/* Inline code */
	:not(pre) > code {
		padding: .1em;
		border-radius: .3em;
		white-space: normal;
	}

	.token.comment,
	.token.block-comment,
	.token.prolog,
	.token.doctype,
	.token.cdata {
		color: $medium-slate;
	}

	.token.punctuation {
		color: $light-slate;
	}

	.token.tag,
	.token.attr-name,
	.token.namespace,
	.token.deleted {
		color: #e2777a;
	}

	.token.function-name {
		color: #6196cc;
	}

	.token.boolean,
	.token.number,
	.token.function {
		color: #f08d49;
	}

	.token.property,
	.token.class-name,
	.token.constant,
	.token.symbol {
		color: #f8c555;
	}

	.token.selector,
	.token.important,
	.token.atrule,
	.token.keyword,
	.token.builtin {
		color: #cc99cd;
	}

	.token.string,
	.token.char,
	.token.attr-value,
	.token.regex,
	.token.variable {
		color: $mint;
	}

	.token.operator,
	.token.entity,
	.token.url {
		color: $skyblue;
	}

	.token.important,
	.token.bold {
		font-weight: bold;
	}
	.token.italic {
		font-style: italic;
	}

	.token.entity {
		cursor: help;
	}

	.token.inserted {
		color: green;
	}

	// pre {
	// 	background-color: #455a64;
	// 	padding: 1rem;
	// 	border-radius: .5rem;
	// 	box-shadow: 0 5px 20px rgba($black, .2);
	// 	text-align: left;
	// 	width: 55vw;
	// 	margin: 2.25em auto;
	// 	white-space: pre-wrap;
	// 	word-break: break-word;

	// 	code {
	// 		color: white;
	// 		font-size: 1.1em;
	// 		line-height: 1;

	// 		&.language-js {
	// 			.hljs {
	// 				&-comment {
	// 					color: #999999;
	// 				}

	// 				&-keyword {
	// 					color: #29ABE2;
	// 					font-weight: bold;
	// 					font-style: italic;
	// 				}

	// 				&-string {
	// 					color: palegoldenrod;
	// 				}

	// 				&-attr {
	// 					color: paleturquoise;
	// 				}

	// 				&-number {
	// 					color: palevioletred;
	// 				}
	// 			}
	// 		}
	// 	}
	// }

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

	img {
		margin: 0 auto;
	}

</style>
