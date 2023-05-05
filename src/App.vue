<script setup>
import { ref } from 'vue'
import Map from '@/components/Map.vue'

const addLocation = () => {
  locations.value.push(formData.value)
}

const formData = ref({
  name: '',
  latitude: '',
  longitude: ''
})

const locations = ref([
  {
    name: 'Tandi',
    latitude: '27.621467',
    longitude: '84.515914'
  },
  {
    name: 'Sauraha Chowk',
    latitude: '27.622584',
    longitude: '84.512324'
  },
  {
    name: 'Export Visa',
    latitude: '27.623858',
    longitude: '84.509095'
  }
])
</script>

<template>
  <main>
    <h1>Nakshatra Demo App</h1>
    <div class="header">
      <form
        action=""
        @submit.prevent="addLocation"
      >
        <div class="input__group">
          <label for="name">Name</label>
          <input
            v-model="formData.name"
            type="text"
            id="name"
          />
        </div>
        <div class="flex">
          <div class="input__group">
            <label for="latitude">Latitude</label>
            <input
              v-model="formData.latitude"
              type="text"
              id="latitude"
            />
          </div>
          <div class="input__group">
            <label for="longitude">Longitude</label>
            <input
              v-model="formData.longitude"
              type="text"
              id="longitude"
            />
          </div>
        </div>
        <p>Note: use valid latitude and longitude data</p>
        <button>Add Marker</button>
      </form>
    </div>
    <Map :locations="locations" />
  </main>
</template>
<style scoped>
button {
  margin-top: 1rem;
  padding: 0.8rem;
  border: none;
  border-radius: 4px;
}
button:hover {
  border: 1px solid green;
  cursor: pointer;
}

form {
  width: 100%;
}

h1 {
  text-align: center;
}
input {
  width: 100%;
  padding: 1rem;
  border-radius: 5px;
  outline: none;
  border: none;
}

label {
  color: #000000;
}

main {
  width: 100%;
}

p {
  font-size: 11px;
  color: rgb(14, 150, 184);
}

.flex {
  display: flex;
  width: 100%;
  gap: 1rem;
}

.header {
  display: flex;
  width: 800px;
  padding: 1rem 2rem;
  background-color: rgb(202, 202, 202);
  margin: 0 auto;
}
.input__group {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 4px;
  margin-top: 0.5rem;
}
</style>
