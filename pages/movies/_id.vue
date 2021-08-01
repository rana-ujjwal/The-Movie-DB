<template>
  <div
    class="backdrop"
    :style="{
      backgroundImage:
        'linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.8)), url(https://image.tmdb.org/t/p/w500/' +
        movie.backdrop_path +
        ')',
    }"
    alt=""
  >
    <div>
      <img
        class="poster"
        :src="'https://image.tmdb.org/t/p/w300/' + movie.poster_path"
        alt=""
      />
    </div>
    <div class="details">
      <div class="title">{{ movie.title }}</div>
      <div class="tagline">{{ movie.tagline }}</div>
      <div class="adult">Adult: {{ movie.adult }}</div>
      <div class="genres">
        <ul>
          <li v-for="genre in movie.genres" :key="genre.id">
            {{ genre.name }}
          </li>
        </ul>
      </div>
      <div class="popularity">
        Popularity <span>{{ movie.popularity }}</span>
      </div>
      <div class="website">
        Website:
        <a :href="movie.homepage" target="_blank"
          ><span>{{ movie.homepage }}</span></a
        >
      </div>
      <div class="runtime">
        Runtime:<span>{{ movie.runtime }}</span>
      </div>
      <div class="row">
        <div class="release-date">
          Realease Date: <span>{{ movie.release_date }}</span>
        </div>
        <div class="status">
          Status: <span>{{ movie.status }}</span>
        </div>
      </div>
      <div class="row">
        <div class="vote-average">
          Vote: <span>{{ movie.vote_average }}</span>
        </div>
        <div class="vote-count">
          Vote-Count: <span>{{ movie.vote_count }}</span>
        </div>
      </div>
      <div class="overview">
        <h2>Overview</h2>
        <span>{{ movie.overview }}</span>
      </div>
      <nuxt-link to="/movies">Back to Movies</nuxt-link>
    </div>    
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      movie: {
          title: "",
          release_date: "",
      },
    };
  },
  async created() {
    const api_key = process.env.TMDB_API;
    try {
      const res = await axios.get(
        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=${api_key}`
      );
      this.movie = res.data;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      title: this.movie.title + "(" + this.movie.release_date.split("-")[0] + ") | The Movie Database",
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
};
</script>

<style>
.backdrop {
  background-repeat: no-repeat;
  background-size: 100% 100%;
  color: #fff;
  padding: 2rem;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  font-size: 1.1rem;
  line-height: 2;
}

.backdrop .details {
  width: calc(100% - 340px);
}

.backdrop span {
  font-size: 1rem;
  color: #ddd;
}

.backdrop .row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.backdrop a {
  color: #ddd;
  text-decoration: underline;
}

.backdrop .poster {
  border-radius: 10px;
  margin-right: 20px;
}

.backdrop .title {
  font-weight: 800;
  font-size: 1.3rem;
}

.backdrop .tagline {
  font-style: italic;
  color: #ddd;
}

.backdrop .overview {
  line-height: 1.6;
}

.backdrop .genres ul li {
  display: inline-block;
  padding: 0.1rem 1rem;
  background-image: linear-gradient(to right, #a7d2b1, #6bbec2);
  box-shadow: 1px 1px 2px #333;
  font-size: 1rem;
  border-radius: 50px;
  margin: 5px;
  color: #000;
}
</style>