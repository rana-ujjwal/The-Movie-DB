<template>
  <form @submit.prevent="onSubmit" class="search-form">
      <input type="text" v-model="text" placeholder="Search movies">
      <input type="submit" value="Search">
  </form>
</template>

<script>
export default {
    name: "Search",
    data() {
        return{
            text: ""
        }
    },
    methods: {
        onSubmit() {
            this.$emit("search-movie", this.text);
            this.text="";
        } 
    }
}
</script>

<style>
.search-form{
    display: flex;
}

.search-form input {
    height: 35px;
    padding: 0 10px;
    border-radius: 0;
    border: 1px solid #ccc;
    outline: none;
}

.search-form input[type="text"] {
    border-right: none;
    border-top-left-radius: 5px;
    border-bottom-left-radius: 5px;
}

.search-form input[type="submit"] {
    border: 0;
    background-color: #6cbec1;
    color: #fff;
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px;
}   
</style>