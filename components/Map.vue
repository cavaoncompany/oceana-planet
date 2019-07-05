<template>
  <div class="container">
    <div class="info">
      <h1>{{ home.header }}</h1>
      <p>
        {{ home.infoBlurb }}
      </p>
    </div>
    <div class="map-container">
      <div
        v-for="(tree, i) in home.locations"
        :key="i"
        class="tree-container"
        :style="
          `marginLeft: ` + tree.lat + `px; marginTop: ` + tree.lng + `px;`
        "
      >
        <img
          :id="'tree' + i"
          class="tree"
          :src="tree.tree"
          :alt="tree.name"
          @mouseover="showInfo('tree-info' + i)"
          @mouseleave="hideInfo('tree-info' + i)"
        />
        <div :id="'tree-info' + i" class="tree-info invisible">
          <h2>{{ tree.name }}</h2>
          <p>{{ tree.info }}</p>
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
      home: home
    }
  },
  methods: {
    showInfo(tooltip) {
      if (process.client) {
        // eslint-disable-next-line
        console.log('in')
        document.getElementById(tooltip).classList.remove('invisible')
      }
    },
    hideInfo(tooltip) {
      if (process.client) {
        // eslint-disable-next-line
        console.log('out')
        document.getElementById(tooltip).classList.add('invisible')
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
  width: 370px;
  font-size: 18px;
}
.info h1 {
  font-size: 24px;
}
.map-container {
  background-image: url('/images/map.png');
  min-height: 500px;
  height: 500px;
  width: 960px;
  margin: 0 auto;
  background-size: contain;
  background-repeat: no-repeat;
  text-align: left;
  position: relative;
}
.tree-container {
  position: absolute;
  z-index: 0;
}
.tree {
  width: auto;
  height: 40px;
  z-index: 150;
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
  z-index: 1;
  border-radius: 8px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.25);
}
.tree-info h2 {
  color: #4e9939;
  font-size: 12px;
  margin-bottom: 5px;
}
.invisible {
  visibility: hidden;
}
</style>
