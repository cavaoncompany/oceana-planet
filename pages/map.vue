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
          :no-wrap="true"
          :zoom="2.4"
          :center="[47.41322, -1.219482]"
        >
          <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png" />
          <l-marker :lat-lng="[47.41322, -1.219482]" />
        </l-map>
      </no-ssr>
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

export default {
  components: {
    Header,
    Footer
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
