<script>

	import router from 'page';

	import Portfolio from './routes/Portfolio.svelte';

	export let name;

	let page;
	let params;

	router('/', () => page = Portfolio);
	router.start();
</script>

<svelte:component this={page} params={params} />

<style>

</style>