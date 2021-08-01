<template>
  <div>
    <h2>About the Movie DB</h2>
    <p>You can find all the information about movies in this site.</p>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "About The Movie Database",
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
</style>