<template>
  <div class="contact">
    <Header page="contact" />
    <div class="contact-content">Contact us</div>
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
.contact {
  margin: 0 auto;
  height: 100vh;
  text-align: center;
  background-color: #60abcb;
  font-family: 'Ubuntu', sans-serif;
}
.contact .contact-content {
  height: 80%;
  padding-top: 50px;
}
</style>
