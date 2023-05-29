<script>
import ResultsList from "./ResultsList.vue";
import { store } from "../store";

export default {
  data() {
    return {
      store,
    };
  },
  components: {
    ResultsList,
  },
};
</script>
<template>
  <div class="container">
    <ResultsList
      listTitle="Risultati dei film"
      :arrCards="store.arrMovies"
      cardType="movie"
    ></ResultsList>

    <ResultsList
      listTitle="Risultati delle serie"
      :arrCards="store.arrSeries"
      cardType="serie"
    ></ResultsList>
  </div>
</template>
<style lang="scss" scoped>
.container {
  width: 80%;
  margin: auto;
  padding: 2rem;
}
</style>
