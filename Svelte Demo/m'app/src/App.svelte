<script>
	export let name;
	import Search from './Search.svelte';
</script>

<main>
	<h1>Welcome to <span class="name">{name}</span>. Try searching for an address.</h1>
	<Search></Search>
</main>

<style>
	@import url('https://fonts.googleapis.com/css?family=Permanent+Marker&display=swap');
	.name { font-family: 'Permanent Marker'; }
</style>