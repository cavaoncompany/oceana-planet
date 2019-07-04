<template>
  <div class="container">
    <div class="info">
      <h1>We are one.</h1>
      <p>
        Together we can make a difference to make changes to global warming.
      </p>
    </div>
    <div id="map-wrap" style="height: 100vh">
      <no-ssr>
        <l-map class="mappy" :zoom="2" :center="[47.41322, -1.219482]">
          <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png" />
          <l-marker :lat-lng="[47.41322, -1.219482]" />
        </l-map>
      </no-ssr>
    </div>
  </div>
</template>

<style>
.container {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
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
.mappy {
  height: 100%;
  width: 100%;
}
</style>
