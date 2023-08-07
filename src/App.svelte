<script>
	export let name;
	import Slideshow from './Slideshow.svelte';
</script>

<main>
	<h1>babbycakes Slideshow App</h1>
	<Slideshow />
	<footer>
		Is this really html footer?
	</footer>
	<b>how can svelte be used to link up to other things?</b>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
