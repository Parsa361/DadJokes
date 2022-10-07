<template>
  <div>
    <h2 class="text-center mt-5">Welcome to the dad jokes page</h2>
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

export default {
  async asyncData() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };
    try {
      let res = await axios.get("https://icanhazdadjoke.com/search", config);
      let jokes = res.data.results;
      return { jokes };
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
  components: {
    Joke,
  },
};
</script>