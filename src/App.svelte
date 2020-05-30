<script>

	import router from 'page';

	import Portfolio from './routes/Portfolio.svelte';
	import Blog from './routes/Blog.svelte';

	let page;
	let params;

	router('/', () => page = Portfolio);
	router('/blog', () => page = Blog);
	router.start();
</script>

<svelte:component this={page} params={params} />

<style>

</style>