<template>
  <div class="about">
    <Header page="about" />
    <div class="about-content">About us</div>
    <Footer />
  </div>
</template>

<script>
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'

export default {
  components: {
    Header,
    Footer
  }
}
</script>

<style>
.about {
  margin: 0 auto;
  height: 100vh;
  text-align: center;
  background-color: #60abcb;
  font-family: 'Ubuntu', sans-serif;
}
.about .about-content {
  height: 80%;
  padding-top: 50px;
}
</style>
