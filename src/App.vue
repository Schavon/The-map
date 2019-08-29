<template>
  <div id="app">
      <TheMap
      ref = ""
      apiKey="VS1qIY9VyCItiEKLqgcq_C2q5WrEk7v2BgIkL2shyGU"></TheMap>
  </div>
</template>

<script>
import TheMap from './components/TheMap.vue'

export default {
  name: 'app',
  components: {
    TheMap
  },
  mounted() {
    let map = this.$refs.map;
    map.dropMarker({ lat: 37.11, lng: -121.11 });
  }
}
</script>

<style>

body {
  margin: 0;
}

</style>
