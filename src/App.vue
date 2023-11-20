<template>
  <NavBar :logo="logo_src" :alt="app_name"/>
  <router-view/>
  <Footer />
</template>

<script>

import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'

export default {
  components: {
    NavBar,
    Footer
  },
  data() {
    return {
      logo_src: "/img/roxinho.jpg",
      app_name: "Roxinho Delivery",
    }
  }
}

</script>

<style>

* {
  font-family: Arial, Helvetica, sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  color: #111;
}

.main-container {
  margin: 250px;
  min-height: 250px;
}

h1 {
  font-size: 42px;
  text-align: center;
  margin-bottom: 30px;
}

</style>
