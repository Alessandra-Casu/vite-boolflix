<script>
import CardComponent from "./CardComponent.vue";

export default {
  props: {
    listTitle: String,
    arrCards: Array,
    cardType: String,
  },
  components: {
    CardComponent,
  },
  methods: {
    formatObj(originalObj) {
      switch (this.cardType) {
        case "movie":
          return this.formatObjMovies(originalObj);
          break;
        case "serie":
          return this.formatObjSeries(originalObj);
          break;
      }
    },
    formatObjMovies(originalObj) {
      return {
        title: originalObj.title,
        originalTitle: originalObj.original_title,
        language: originalObj.original_language,
        rating: this.convertRating(originalObj.vote_average, 10, 5),
        image: this.makeURL(originalObj.poster_path),
      };
    },
    formatObjSeries(originalObj) {
      return {
        title: originalObj.name,
        originalTitle: originalObj.original_name,
        language: originalObj.original_language,
        rating: this.convertRating(originalObj.vote_average, 10, 5),
        image: this.makeURL(originalObj.poster_path),
      };
    },
    convertRating(originalRating, originalMax, newMax) {
      return Math.round((originalRating * newMax) / originalMax);
    },
    makeURL(partialPath) {
      return "https://image.tmdb.org/t/p/w342" + partialPath;
    },
  },
};
</script>

<template>
  <h2>{{ listTitle }}</h2>
  <CardComponent
    v-for="card in arrCards"
    :key="card.id"
    :cardData="formatObj(card)"
  ></CardComponent>
</template>
<style></style>
