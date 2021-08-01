<template>
  <div>
    <h2>Welcome to The Movies Database where you can find all the related details about movies.</h2>
  </div>
</template>

<script>
export default {
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
};
</script>

<style>
</style>