<template>
  <div>
    <div class="search-bar">
      <div v-if="total_results != 0">
        <b>{{ total_results }}</b><span>movies found.</span>
      </div>
      <Search v-on:search-movie="searchMovie" />
    </div>
    <div class="movies">
      <Movie v-for="movie in movies" :key="movie.id" :movie="movie" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Movie from "../../components/Movie.vue";
import Search from "../../components/Search.vue";
export default {
  components: {
    Movie,
  },
  data() {
    return {
      movies: [],
      total_results: 0,
    };
  },
  async created() {
    const api_key = process.env.TMDB_API;
    try {
      const res = await axios.get(
        `https://api.themoviedb.org/3/movie/upcoming?api_key=${api_key}`
      );
      this.movies = res.data.results;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      title: "The Movie Database",
      meta: [
        {
          hid: "description",
          name: "description",
          content:
            "This site provides latest and greatest information about the movies.",
        },
      ],
    };
  },
  methods: {
    async searchMovie(text) {
      const api_key = process.env.TMDB_API;
      try {
        const res = await axios.get(
          `https://api.themoviedb.org/3/search/movie?api_key=${api_key}&query=${text}&include_adult=false`
        );
        this.movies = res.data.results;
        this.total_results = res.data.total_results;
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style>
.movies {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.search-bar {
  display: flex;
  align-items: center;
  margin: 10px 0;
}
.search-bar span {
  margin: 0 0.3rem;
}
</style>