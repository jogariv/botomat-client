<template>
  <div id="app">
    <main role="main" class="container">
      <robos v-if="loaded" :roboList="robosData"></robos>
      <span class="alert alert-danger" v-else>Something went wrong!... Please verify if the <strong>botomAPI</strong> service is running.</span>
    </main>
  </div>
</template>

<script>

import Robos from '@/components/Robos.vue'
const API_URL = "http://localhost:8081/robots";

export default {
  name: 'App',
  components: {
    Robos
  },
  data() {
    return{
      robosData: [],
      loaded: false
    }
  },
  created() {
    fetch(API_URL)
      .then(response => response.json())
      .then(result => {
        this.robosData = result.response.robos;
        this.loaded = true;
      });
  }
}
</script>