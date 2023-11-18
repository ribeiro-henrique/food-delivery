<template>
  <Banner />
  <div class="main-container">
    <h1>Monte o seu Burguer:</h1>
    <BurguerForm />
  </div>
</template>

<script>
import Banner from '../components/Banner.vue';
import BurguerForm from '../components/BurgerForm.vue';

export default {
  name: "Homer",
  components: {
    Banner,
    BurguerForm,
  }
}

</script>
