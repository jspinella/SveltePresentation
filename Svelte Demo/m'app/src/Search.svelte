<script>
    const apiUrl = 'https://nominatim.openstreetmap.org/search?format=json&q=';
    let results = [];
    let query = '';
    let promise = query && queryNominatim(query);

    async function queryNominatim(query) {
        const response = await fetch(apiUrl + query);
        const result = await response.text();

        if (response.ok) {
			return JSON.parse(result);
		} else {
			throw new Error(result);
		}
    }

    function handleClick() {
        promise = queryNominatim(query);
    }
</script>

<style>
    input {
        font-size: 1.5rem;
        padding: 1rem;
        width: 75%;
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

    .results {
        margin-top: 3rem;
    }

    .result {
        font-size: 1.25rem;
        padding: 0.5rem;
    }
</style>

<input bind:value={query}>
<button on:click={() => query && handleClick()}>Search</button>

{#await promise}
	<p>searching</p>
{:then results}
	<div class="results">
    {#each results as result}
        <div class="result">
            {result.display_name}
        </div>
    {/each}
</div>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

