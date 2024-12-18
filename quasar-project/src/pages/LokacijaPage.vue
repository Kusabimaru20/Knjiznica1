<template>
  <q-page class="flex flex-center">
    <div id="map" style="height: 100vh;"></div> <!-- Postavljanje visine karte na 100vh -->
  </q-page>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import * as L from 'leaflet'; // Uvoz Leaflet paketa
import "leaflet/dist/leaflet.css"; // Uvoz stilova za Leaflet

const initialMap = ref(null); // Definiranje reaktivne varijable za kartu

onMounted(() => {
    // Postavljanje karte
    initialMap.value = L.map('map').setView([45.3312, 14.4322], 13);
    
    // Dodavanje OpenStreetMap sloja
    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 19,
        attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
    }).addTo(initialMap.value);

    // Dodavanje markera
    const marker = L.marker([45.3312, 14.4322]).addTo(initialMap.value);
    marker.bindPopup('<b>Knjižnica Rijeka</b><br>Ovdje se nalazimo.').openPopup();
});
</script>

<style scoped>
#map {
    height: 100vh; /* Visina karte na 100% visine prozora */
    width: 100%;   /* Širina karte */
}
</style>
