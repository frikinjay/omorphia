<script context="module" lang="ts">
	import { addMessages, init } from 'svelte-intl-precompile'
	import en from '$locales/en'
	addMessages('en', en)
	init({
		initialLocale: 'en',
		fallbackLocale: 'en',
	})
</script>

<script lang="ts">
	import 'omorphia/styles.postcss'
	import '../styles/prism-one-dark.css'
	import '../styles/gh-markdown.postcss'
	import Sidebar from '../components/Sidebar.svelte'
	import Header from '../components/Header.svelte'
</script>

<div class="app theme-light">
	<Header />
	<Sidebar />
	<main class="app__content">
		<article>
			<slot />
		</article>
	</main>
</div>

<style lang="postcss">
	:global {
		html {
			overflow-y: scroll;
		}

		body {
			margin: 0;
			font-size: var(--font-size);
			font-family: var(--body-font);

			--accent-color: hsl(331, 80%, 45%);
			--accent-color-transparent: hsla(331, 80%, 45%, 0.15);
		}
	}

	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		overflow: hidden;
		background-color: var(--color-bg);

		--sidebar-width: 275px;

		&__content {
			@media (--md) {
				padding-left: var(--sidebar-width);
			}
			overflow-x: hidden;
			overflow-y: auto;

			article {
				max-width: 800px;
				padding-block: 9rem 4rem;
				padding-inline: 24px;

				@media (--sm) {
					padding-inline: 48px;
					padding-block: 9rem 24px;
				}
			}
		}
	}
</style>
