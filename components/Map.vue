<template>
  <div class="container">
    <div class="info">
      <h1>We are one.</h1>
      <p>
        Together we can make a difference to make changes to global warming.
      </p>
    </div>
    <div class="map-container">
      <img
        id="tree1"
        class="tree"
        src="/images/tree-large-round.png"
        alt="big tree"
      />
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
</style>
