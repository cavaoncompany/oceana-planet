<template>
  <div class="container">
    <Header page="map" />
    <div class="info">
      <h1>We are one.</h1>
      <p>
        Together we can make a difference to make changes to global warming.
      </p>
    </div>
    <div id="map" class="map">
      <no-ssr>
        <l-map
          class="mappy"
          :zoom="zoom"
          :center="center"
          :options="mapOptions"
          @update:center="centerUpdate"
          @update:zoom="zoomUpdate"
        >
          <l-tile-layer
            :url="url"
            :attribution="attribution"
            no-wrap:true
          />
          <!-- <l-marker :lat-lng="withPopup">
            <l-popup>
              <div @click="innerClick">
                Scandinavia
                <p v-show="showParagraph">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
                  sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
                  Donec finibus semper metus id malesuada.
                </p>
              </div>
            </l-popup>
          </l-marker> -->
          <l-marker v-for="(tree, i) in locations" :key="i" :lat-lng="tree.latLng">
            <l-popup class="tree-info">
              <div @click="innerClick">
                <h2>{{ tree.title }}</h2>
                <p v-show="showParagraph">
                  {{ tree.info }}
                </p>
              </div>
            </l-popup>
          </l-marker>
          <!-- <l-marker :lat-lng="withTooltip">
            <l-tooltip :options="{ permanent: true, interactive: true }">
              <div @click="innerClick">
                Singapore
                <p v-show="showParagraph">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
                  sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
                  Donec finibus semper metus id malesuada.
                </p>
              </div>
            </l-tooltip>
          </l-marker> -->
        </l-map>
      </no-ssr>
    </div>
    <Footer />
  </div>
</template>

<script>

import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import homepage from '../content/homepage.json'

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
      homepage: homepage,
      zoom: 1.45,
      center: {},
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      withPopup: {},
      withTooltip: {},
      currentZoom: 11.5,
      currentCenter: {},
      showParagraph: true,
      locations: [],
      mapOptions: {
        zoomSnap: 0.5
      }
    }
  },
  created() {
    if (process.client) {
      this.center = leaflet.latLng(22.41322, -1.219482)
      this.withPopup = leaflet.latLng(47.41322, -1.219482)
      this.withTooltip = leaflet.latLng(64.41422, -1.250482)
      this.currentCenter = leaflet.latLng(47.41322, -1.219482)
      this.createTrees()
    }
  },
  methods: {
    createTrees() {
      for (let i = 0; i < this.homepage.maplocations.length; i++) {
        this.locations.push(
          {
            title: homepage.maplocations[i].name,
            info: homepage.maplocations[i].info,
            latLng: leaflet.latLng(Number(homepage.maplocations[i].lat), Number(homepage.maplocations[i].lng))
          }
        )
      }
    },
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
  justify-content: space-between;
  align-items: center;
  text-align: center;
  color: #15468e;
  background-color: rgba(171, 210, 222, 1);
}
.info {
  margin: 50px 0 10px;
  width: 370px;
  font-size: 18px;
}
.info h1 {
  font-size: 24px;
}
#map {
  height: 70vh;
  width: 70%;
  margin: 0 auto;
}
.mappy {
  height: 100%;
  width: 100%;
  background: rgba(171, 210, 222, 1);
}
.leaflet-popup-content {
  width: 150px !important;
}
.tree-info {
  font-size: 12px;
  color: #111;
  background: #ffffff url('/images/tree-large-semi-transparent.png');
  background-repeat: no-repeat;
  background-position-x: 65px;
  background-position-y: 10px;
}
.tree-info h2 {
  color: #4e9939;
  font-size: 12px;
  margin-bottom: 5px;
}
.leaflet-control-container {
  display: none;
}
</style>
