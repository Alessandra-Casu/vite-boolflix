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
          console.log(response.data.results);
          if (response.request.responseURL.includes("/search/movie")) {
            this.store.arrMovies = response.data.results;
          } else {
            this.store.arrSeries = response.data.results;
          } // TO DO scrivere il valore di varResult
        });
    },
    searchToApi(searchStr) {
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
  <AppHeader @searchRequest="searchToApi"></AppHeader>
  <AppMain></AppMain>
</template>

<style></style>
