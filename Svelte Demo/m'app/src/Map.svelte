<script>
    export let location;
    import { onMount } from 'svelte';

    function initMap() {
        var mymap = L.map('mapid').setView([location.lat, location.lon], 15);

        // Use OSM as the map tile provider
        L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors, hey you can put anything here!'
        }).addTo(mymap);
    };

    onMount(async () => {
        console.log('Map onMount');
		initMap();
	});
</script>

<style>
    #mapid { 
        height: 300px;
        margin-top: 2rem;
        border: 0.1rem solid #333;
    }
</style>

<div id="mapid"></div>
