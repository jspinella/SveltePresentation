<script>
    export let location = {};
    console.log(`location coordinates: ${location.lat}, ${location.lon}`);
</script>

<style>
    .map-container {
        margin-top: 2rem;
        border: 0.1rem solid #333;
    }

    #mapid { height: 400px; }

    #lat, #lon {
        display: none;
    }
</style>


<div class="map-container">
    <div id="mapid"></div>
    <div id="lat">{location.lat}</div>
    <div id="lon">{location.lon}</div>

    <script>
        var lat = document.getElementById('lat').innerHTML;
        var lon = document.getElementById('lon').innerHTML;
        var mymap = L.map('mapid').setView([lat, lon], 15);

        // Use OSM as the map tile provider
        L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors, hey you can put anything here!'
        }).addTo(mymap);
    </script>
</div>

