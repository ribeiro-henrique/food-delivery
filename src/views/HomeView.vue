<template>
  <Banner />
  <div class="main-container">
    <h1>Monte seu Açaí:</h1>
    <PurpleForm />
  </div>
</template>

<script>
import Banner from '../components/Banner.vue';
import PurpleForm from '../components/PurpleForm.vue';

export default {
  name: "Homer",
  components: {
    Banner,
    PurpleForm,
  }
}

</script>
