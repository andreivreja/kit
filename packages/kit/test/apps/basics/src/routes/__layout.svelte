<script context="module">
	/** @type {import('@sveltejs/kit').Load} */
	export async function load() {
		return {
			props: {
				foo: {
					bar: 'Custom layout'
				}
			}
		};
	}
</script>

<script>
	import {
		goto,
		invalidate,
		prefetch,
		prefetchRoutes,
		beforeNavigate,
		afterNavigate
	} from '$app/navigation';

	if (typeof window !== 'undefined') {
		Object.assign(window, {
			goto,
			invalidate,
			prefetch,
			prefetchRoutes,
			beforeNavigate,
			afterNavigate
		});
	}

	/** @type {{ bar: string }} */
	export let foo;
</script>

<slot />

<footer>{foo.bar}</footer>

<style>
	footer {
		color: purple;
	}
</style>
