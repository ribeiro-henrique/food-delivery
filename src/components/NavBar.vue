<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link> 
    <router-link to="/pedidos">Pedidos</router-link>
  </div>

</template>

<script>
  export default {
    name: "NavBar",
    props: ["logo", "alt"]
  }

</script>

<style scoped>
  #nav {
    background-color: #371B34;
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }

  #nav #logo-url {
    margin: auto;
    margin-left: 0;
  }

  #logo {
    height: 70px;
    width: 70px;
  }

  #nav a {
    color: #fcba03;
    text-decoration: none;
    margin: 12px;
    transition: 0.5s;
    font-weight: 700;
  }

  #nav a:hover {
    color: #fff;
  }

</style>