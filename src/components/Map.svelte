<script>
  import { onMount, onDestroy } from "svelte";
  import { Map, NavigationControl, Marker, Popup } from "maplibre-gl";
  import "maplibre-gl/dist/maplibre-gl.css";
  import { markers } from "../data/markers";

  let map;
  let mapContainer;

  onMount(() => {
    const initialState = { lng: -0.08533793, lat: 51.5163853635, zoom: 10.5 };

    map = new Map({
      container: mapContainer,
      style: "https://basemaps.cartocdn.com/gl/positron-gl-style/style.json",
      center: [initialState.lng, initialState.lat],
      zoom: initialState.zoom,
    });

    map.addControl(new NavigationControl(), "top-right");

    for (const marker of markers) {
      new Marker({ color: marker.color })
        .setLngLat([marker.lng, marker.lat])
        .addTo(map)
        .setPopup(new Popup({ offset: 25 }).setText(marker.popup));
    }
  });

  onDestroy(() => {
    map.remove();
  });
</script>

<div class="map-wrap">
  <div class="map" id="map" bind:this={mapContainer}></div>
</div>

<style>
  .map-wrap {
    position: relative;
    width: 100%;
    height: 77vh;
  }

  .map {
    position: absolute;
    width: 100%;
    height: 100%;
  }
</style>
