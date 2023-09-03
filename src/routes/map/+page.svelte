<script>
  import { onMount } from 'svelte';
  import Map from 'ol/Map';
  import View from 'ol/View';
  import TileLayer from 'ol/layer/Tile';
  import OSM from 'ol/source/OSM';
  import VectorLayer from 'ol/layer/Vector';
  import VectorSource from 'ol/source/Vector';
  import GeoJSON from 'ol/format/GeoJSON';
  import Style from 'ol/style/Style';
  import Fill from 'ol/style/Fill';

  let map;

  onMount(() => {
    const mapContainer = document.getElementById('map');

    // Create a base layer with OpenStreetMap tiles
    const baseLayer = new TileLayer({
      source: new OSM(),
    });

    // Create a vector layer for displaying GeoJSON data
    const vectorSource = new VectorSource({
      format: new GeoJSON(),
      url: 'countries.geojson',
    });

    const vectorLayer = new VectorLayer({
      source: vectorSource,
      style: new Style({
        fill: new Fill({
          color: 'rgba(0, 106, 78, 0.75)',
        }),
      }),
    });

    // Set up the map view
    map = new Map({
      layers: [baseLayer, vectorLayer],
      target: mapContainer,
      view: new View({
        center: [0, 0],
        zoom: 2,
      }),
    });
  });
</script>

<style>
  #map {
    width: 100%;
    height: 100vh;
  }
</style>

<div id="map"></div>
