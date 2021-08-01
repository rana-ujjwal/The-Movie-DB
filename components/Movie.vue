<template>
  <nuxt-link :to="'/movies/'+movie.id">
    <div class="movie">
      <img
        :src="'https://image.tmdb.org/t/p/w200/' + movie.poster_path"
        alt=""
      />
      <div class="title">{{ movie.title }}</div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Movie",
  props: ["movie"],
};
</script>

<style>
.movie {
  width: 200px;
  margin: 1rem;  
}
.movie img {
  background: #ccc;
  height: 300px;
  width: 200px;
}
</style>