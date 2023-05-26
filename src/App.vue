<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

import axios from "axios";
import { store } from "./store";

export default {
  data() {
    return {
      store,
    };
  },
  components: {
    AppHeader,
    AppMain,
  },
  methods: {
    requestToApi(searchStr) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "91c0f3fc838603e06ffe5972c76dbab9",
            query: searchStr,
          },
        })
        .then((response) => {
          console.log(response.data.results);
          this.store.arrMovies = response.data.results;
        });
    },
  },
};
</script>

<template>
  <AppHeader @searchRequest="requestToApi"></AppHeader>
  <AppMain></AppMain>
</template>

<style></style>
