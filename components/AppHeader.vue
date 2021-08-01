<template>
  <header class="header">
    <div class="title">
      <img src="/logo.svg" />
      <h1>The Movie DB</h1>
    </div>
    <ul>
      <li><nuxt-link to="/">Home</nuxt-link></li>
      <li><nuxt-link to="/movies">Movies</nuxt-link></li>      
      <li><nuxt-link to="/about">About</nuxt-link></li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
};
</script>

<style>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px dotted #ccc;
}

.title {
  display: flex;
  align-items: center;
}

.title img {
  height: 50px;
  margin-right: 2rem;
}

.title h1 {
  font-size: 2rem;
  color: #6cbec1;
}

.header ul li {
  display: inline-block;  
}

.header ul li a{
  background: #333;
  padding: 0.3rem 1rem;
  margin-right: 0.5rem;
  color: #fff;
}

</style>