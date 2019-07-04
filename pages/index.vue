<template>
  <div class="container">
    <Header />
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
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #60abcb;
  font-family: 'Ubuntu', sans-serif;
}
</style>
