<template>
  <form @submit.prevent="onSubmit">
    <input
      class="search-box"
      type="text"
      v-model="text"
      placeholder="Search Jokes..."
    />
    <input type="submit" value="Search Jokes" />
  </form>
</template>

<script>
export default {
  name: "SearchJokes",
  data() {
    return {
      text: ""
    };
  },
  methods: {
    onSubmit() {
      this.$emit("search-text", this.text);
      this.text = "";
    }
  }
};
</script>

<style scoped>
.search-box {
  border: 1px solid white;
  color: white;
}
</style>
