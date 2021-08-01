<template>
<div class="container">  
  <AppHeader />
  <Nuxt />
</div>
</template>

<script>
import AppHeader from "../components/AppHeader.vue";
export default {
  components: {
    AppHeader
  }
}
</script>

<style>

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  background-color: #f4f4f4;
  font-size: 1rem;
  line-height: 1.6;
  font-family: Arial, Helvetica, sans-serif;
}

.container {
  max-width: 1000px;
  background-color: white;
  margin: 2rem auto;
  padding: 1rem 2rem;
}

a {
  text-decoration: none;
  color: #333;
}

ul {
  list-style: none;
}

</style>