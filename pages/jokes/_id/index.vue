<template>
  <div>
    <nuxt-link to="/jokes" style="color: black">
      <h4 class="text-center mt-5">Back To Jokes</h4>
    </nuxt-link>
    <p class="mt-5 text-center">{{ joke }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: {},
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };
    try {
      let res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );
      this.joke = res.data.joke;
    } catch (error) {
      console.log(error);
    }
  },
  head() {
    return {
      title: this.joke,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Enjoy From Dad Jokes",
        },
      ],
    };
  },
};
</script>
