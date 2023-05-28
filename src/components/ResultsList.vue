<script>
import CardComponent from "./CardComponent.vue";
export default {
  components: { CardComponent },
  props: {
    listTitle: String,
    arrCards: Array,
    cardType: String,
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

    formatTObjMovies(originalObj) {
      return {
        title: originalObj.title,
        originalTitle: originalObj.original_title,
        language: originalObj.original_language,
        rating: this.convertRating(originalObj.voto_average, 10, 5),
        image: this.makeUrl(originalObj.poster_path),
      };
    },
    formatTObjSeries(originalObj) {
      return {
        title: originalObj.name,
        originalTitle: originalObj.original_name,
        language: originalObj.original_language,
        rating: this.convertRating(originalObj.voto_average, 10, 5),
        image: this.makeUrl(originalObj.poster_path),
      };
    },
    convertRating(originalRating, originalMax, newMax) {
      //originalRating : 10 = newRating : 5
      return Math.round((originalRating * newMax) / originalMax);
    },
    makeUrl(partialPath) {
      return partialPath
        ? "https://image.tmdb.org/t/p/w342" + partialPath
        : "/img/Not.png";
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
