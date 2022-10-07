<template>
  <div>
    <h2 class="text-center mt-5">Welcome to the dad jokes page</h2>
    <search-jokes class="mt-5" v-on:search-text="searchText" />
    <hr />
    <Joke
      v-for="joke in jokes"
      :key="joke.id"
      :id="joke.id"
      :joke="joke.joke"
    />
    <br />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "~/components/Joke.vue";
import SearchJokes from "~/components/SearchJokes.vue";

export default {
  data() {
    return {
      jokes: [],
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };
    try {
      let res = await axios.get("https://icanhazdadjoke.com/search", config);
      this.jokes = res.data.results;
    } catch (error) {
      console.log(error);
    }
  },
  head() {
    return {
      title: "Jokes Page",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Enjoy From Dad Jokes",
        },
      ],
    };
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json",
        },
      };
      try {
        console.log(text);
        let res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
        this.jokes = res.data.results;
      } catch (error) {
        console.log(error);
      }
    },
  },
  components: {
    Joke,
    SearchJokes,
  },
};
</script>