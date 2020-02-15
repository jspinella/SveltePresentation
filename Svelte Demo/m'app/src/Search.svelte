<script>
	import Map from './Map.svelte';
    const apiUrl = `https://nominatim.openstreetmap.org/search?format=json&limit=1&q=`;
    let query;
    let promise;

    function handleClick() {
        promise = queryNominatim(query);
    }

    async function queryNominatim(query) {
        const response = await fetch(apiUrl + query);
        const result = await response.text();

        if (response.ok) {
            console.log('response is ok!');
			return JSON.parse(result)[0];
		} else {
            console.log('oh no!');
			throw new Error(result);
		}
    }
</script>

<style>
    input {
        font-size: 1.5rem;
        padding: 1rem;
        width: 60%;
    }

    button {
        font-size: 2rem;
        background: none;
        border: none;
        text-decoration: underline;
        cursor: pointer;
    }

    p {
        font-size: 1.5rem;
    }

    .error {
        color: red;
    }
</style>

<input bind:value={query}>
<button on:click={() => query && handleClick()}>Search</button>

<!-- TODO: Await Block! -->
