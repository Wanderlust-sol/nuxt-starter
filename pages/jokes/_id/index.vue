<template>
  <div>
    <nuxt-link to="/about">Back to Jokes</nuxt-link>
    <h2>{{ this.joke }}</h2>
    <hr />
    <small>Joke ID: {{ this.$route.params.id }}</small>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      joke: {}
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );

      console.log(res.data);
      this.joke = res.data.joke;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      titile: this.joke,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for joke"
        }
      ]
    };
  }
};
</script>

<style scoped></style>
