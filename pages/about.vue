<template>
  <div>
    <h1>About ME?</h1>
    <p>This is an app that displays my info</p>
    <Joke
      v-for="joke in jokes"
      :key="joke.id"
      :id="joke.id"
      :joke="joke.joke"
    ></Joke>
  </div>
</template>

<script>
import axios from "axios";
import Joke from "@/components/Joke";

export default {
  components: { Joke },
  data() {
    return {
      jokes: []
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", config);

      console.log(res.data);
      this.jokes = res.data.results;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      titile: "About The APP",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for me"
        }
      ]
    };
  }
};
</script>

<style scoped></style>
