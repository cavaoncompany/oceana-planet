<template>
  <div class="container">
    <div class="info">
      <h1>{{ home.header }}</h1>
      <p>
        {{ home.infoBlurb }}
      </p>
    </div>
    <div class="map-container-wrapper">
      <div class="map-container">
        <img class="world-map" src="/images/map.png" alt="world map">
        <div
          v-for="(tree, i) in home.locations"
          :key="i"
          class="tree-container"
          :style="
            `marginLeft: ` + tree.lat + `%; marginTop: ` + tree.lng + `%;`
          "
        >
          <img
            :id="'tree' + i"
            class="tree"
            :src="tree.tree"
            :alt="tree.name"
            @mouseover="showInfo('tree-info' + i, 'tree' + i, tree.treeOnHover)"
            @mouseleave="hideInfo('tree-info' + i, 'tree' + i, tree.tree)"
          />
          <div
            :id="'tree-info' + i"
            class="tree-info invisible"
            :class="{'right-align' : tree.lat > 50}"
          >
            <h2>{{ tree.name }}</h2>
            <p>{{ tree.info }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import home from '../content/homepage.json'
export default {
  data() {
    return {
      home: home,
      windowWidth: 0,
      windowHeight: 0
    }
  },
  created() {
    if (process.client) {
      // eslint-disable-next-line
      window.addEventListener('resize', this.getWindowSize)
    }
  },
  methods: {
    showInfo(tooltip, img, src) {
      if (process.client) {
        document.getElementById(tooltip).classList.remove('invisible')
        document.getElementById(img).src = src
      }
    },
    hideInfo(tooltip, img, src) {
      if (process.client) {
        document.getElementById(tooltip).classList.add('invisible')
        document.getElementById(img).src = src
      }
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
  color: #15468e;
}
.info {
  margin: 50px 0;
  max-width: 370px;
  font-size: 18px;
  height: 100px !important;
}
.info h1 {
  font-size: 24px;
}
.map-container {
  margin: 0 auto;
  background-size: cover;
  background-repeat: no-repeat;
  text-align: left;
  position: relative;
  display: inline-block;
}
.map-container .world-map {
  width: 100%;
  z-index: -1;
}
.tree-container {
  position: absolute;
  z-index: 10;
  height: 8%;
  width: 20px;
}
.tree {
  width: auto;
  height: 100%;
  z-index: 140;
}
.tree-info {
  font-size: 12px;
  color: #111;
  background: #ffffff url('/images/tree-large-semi-transparent.png');
  background-repeat: no-repeat;
  background-position-x: 65px;
  background-position-y: 10px;
  width: 150px;
  padding: 20px;
  z-index: 156;
  border-radius: 8px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.25);
  height: 100px !important;
}
.tree-info h2 {
  color: #4e9939;
  font-size: 12px;
  margin-bottom: 5px;
}
.invisible {
  visibility: hidden;
}
.right-align {
  position: absolute;
  right: 0;
}
</style>
