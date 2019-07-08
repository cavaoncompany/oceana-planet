<template>
  <div class="container">
    <Header page="map" />
    <div class="info">
      <h1>We are one.</h1>
      <p>
        Together we can make a difference to make changes to global warming.
      </p>
    </div>
    <div id="map-wrap">
      <no-ssr>
        <l-map
          class="mappy"
          :zoom="zoom"
          :center="center"
          :options="mapOptions"
          style="height: 80%"
          @update:center="centerUpdate"
          @update:zoom="zoomUpdate"
        >
          <l-tile-layer :url="url" :attribution="attribution" />
          <l-marker :lat-lng="withPopup">
            <l-popup>
              <div @click="innerClick">
                I am a popup
                <p v-show="showParagraph">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
                  sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
                  Donec finibus semper metus id malesuada.
                </p>
              </div>
            </l-popup>
          </l-marker>
          <l-marker :lat-lng="withTooltip">
            <l-tooltip :options="{ permanent: true, interactive: true }">
              <div @click="innerClick">
                I am a tooltip
                <p v-show="showParagraph">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
                  sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
                  Donec finibus semper metus id malesuada.
                </p>
              </div>
            </l-tooltip>
          </l-marker>
        </l-map>
      </no-ssr>
    </div>
    <Footer />
  </div>
</template>

<script>

import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
// import { LMap, LTileLayer, LMarker, LPopup, LTooltip } from '~/plugins/leaflet.js'
// const isBrowser = typeof window !== 'undefined'
let leaflet
if (process.client) {
  leaflet = require('leaflet')
}

export default {
  components: {
    Header,
    Footer
  },
  data() {
    return {
      zoom: 13,
      center: {},
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      withPopup: {},
      withTooltip: {},
      currentZoom: 11.5,
      currentCenter: {},
      showParagraph: false,
      mapOptions: {
        zoomSnap: 0.5
      }
    }
  },
  created() {
    if (process.client) {
      this.center = leaflet.latLng(47.41322, -1.219482)
      this.withPopup = leaflet.latLng(47.41322, -1.219482)
      this.withTooltip = leaflet.latLng(47.41422, -1.250482)
      this.currentCenter = leaflet.latLng(47.41322, -1.219482)
    }
  },
  methods: {
    zoomUpdate(zoom) {
      this.currentZoom = zoom
    },
    centerUpdate(center) {
      this.currentCenter = center
    },
    showLongText() {
      this.showParagraph = !this.showParagraph
    },
    innerClick() {
      alert('Click!')
    }
  }
}
</script>

<style>
.container {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: #15468e;
  background-color: rgba(178, 210, 221, 1);
}
.info {
  margin: 50px 0;
  width: 370px;
  font-size: 18px;
}
.info h1 {
  font-size: 24px;
}
.map-container {
  background-image: url('/images/map.png');
  height: 100%;
  width: 960px;
  margin: 0 auto;
  background-size: contain;
  background-repeat: no-repeat;
}
#tree1 {
  height: 50px;
}
#map-wrap {
  height: 70vh;
  width: 80%;
  margin: 0 auto;
}
.mappy {
  height: 100%;
  width: 100%;
}
</style>
