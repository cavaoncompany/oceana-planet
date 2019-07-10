<template>
  <div class="container">
    <Header page="home" />
    <Map />
    <Footer />
  </div>
</template>

<script>
import Map from '~/components/Map.vue'
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'

export default {
  components: {
    Map,
    Header,
    Footer
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #60abcb;
  font-family: 'Ubuntu', sans-serif;
}
/* * {
    background: #000 !important;
    color: #0f0 !important;
    outline: solid #f00 1px !important;
  } */
</style>
