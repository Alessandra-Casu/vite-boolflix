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
    requestToApi(url, objParams, varResult) {
      axios
        .get(url, {
          params: objParams,
        })
        .then((response) => {
          console.log(response);
          if (response.request.responseURL.includes("/search/movie")) {
            this.store.arrMovies = response.data.results;
          } else {
            this.store.arrSeries = response.data.results;
          } // TO DO prendere il valore di VArResult
        });
    },
    searchApi(searchStr) {
      const objParams = {
        api_key: "91c0f3fc838603e06ffe5972c76dbab9",
        query: searchStr,
      };
      this.requestToApi(
        "https://api.themoviedb.org/3/search/movie",
        objParams,
        this.store.arrMovies
      ); //per i film
      this.requestToApi(
        "https://api.themoviedb.org/3/search/tv",
        objParams,
        this.store.arrSeries
      ); //per le serie
    },
  },
};
</script>

<template>
  <AppHeader @searchRequest="searchApi" />

  <AppMain></AppMain>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: rgb(53, 52, 52);
}
</style>
