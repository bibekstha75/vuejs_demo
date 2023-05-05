<script setup>
import { LMap, LTileLayer, LMarker, LTooltip } from '@vue-leaflet/vue-leaflet'
import { onMounted, ref } from 'vue'

import 'leaflet/dist/leaflet.css'

defineProps({
  locations: {
    type: Object,
    default: {}
  }
})

//default center postion for map.
const mapCenter = ref([27.621467, 84.515914])
const zoom = 13

const setCurrentLocation = () => {
  navigator.geolocation.getCurrentPosition((pos) => {
    mapCenter.value = [pos.coords.latitude, pos.coords.longitude]
  })
}

onMounted(() => {
  //uncomment to use location of user as default location
  //   setCurrentLocation()
})
</script>

<template>
  <div style="height: 400px; width: 800px">
    <l-map
      :use-global-leaflet="false"
      ref="map"
      v-model:zoom="zoom"
      :center="mapCenter"
    >
      <l-tile-layer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        layer-type="base"
        name="OpenStreetMap"
      >
      </l-tile-layer>

      <l-marker
        :key="index"
        v-if="locations"
        v-for="(location, index) in locations"
        :lat-lng="[location.latitude, location.longitude]"
      >
        <l-tooltip> {{ location.name }} </l-tooltip>
      </l-marker>
    </l-map>
  </div>
</template>
