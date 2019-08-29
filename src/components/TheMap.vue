<template>
 <div>
<div ref="map" id="map"></div>

</div>
</template>

<script>
export default {
  name: 'TheMap',
  props: {
    apiKey: String
  },
  data() {
    return {
      platform: {},
      map: {}
    }
  },

  created() {
    this.platform = new H.service.Platform({
      apikey: this.apiKey
    });
  },
  mounted() {
    this.map = new H.Map(
      this.$refs.map,
      this.platform.createDefaultLayers().vector.normal.map,
      {
        center: { lat: 37, lng: -121 },
        zoom: 10
      }
    );
    let mapEvent = new H.mapevents.MapEvents(this.map);
    let behavior = new H.mapevents.Behavior(mapEvent);
    this.dropMarker({ lat: 37, lng: 121});
  },
  methods: {
    dropMarker(position) {
      let marker = new H.map.Marker(position);
      this.map.addObject(marker);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#map {
  width: 100vw;
  height: 100vh;
  background-color: silver;
}

</style>
