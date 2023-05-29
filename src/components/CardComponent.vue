<script>
import LangFlag from "vue-lang-code-flags/LangFlag.vue";
export default {
  props: {
    cardData: Object,
  },
  components: {
    LangFlag,
  },
};
</script>
<template>
  <div class="cardMovieSerie">
    <ul>
      <img class="image" :src="cardData.image" :alt="cardData.title" />
      <div class="retro-card">
        <li>{{ cardData.title }}</li>
        <li>{{ cardData.originalTitle }}</li>
        <li>
          <LangFlag :iso="cardData.language" :squared="false" />
          <span class="lang-text">{{ cardData.language }}</span>
        </li>
        <li>
          <font-awesome-icon
            icon="fa-solid fa-star"
            v-for="i in cardData.rating"
            :key="i"
            class="star"
          ></font-awesome-icon>
          <font-awesome-icon
            icon="fa-regular fa-star "
            v-for="i in 5 - cardData.rating"
            :key="i"
            class="star"
          ></font-awesome-icon>
        </li>
        <li>{{ cardData.overview }}</li>
      </div>
    </ul>
  </div>
</template>
<style lang="scss" scoped>
.lang-text {
  display: none;
}
.flag-icon-undefined {
  display: none;
}
.flag-icon-undefined + .lang-text {
  display: inline;
}

.cardMovieSerie {
  width: 25%;
  margin: 1rem;
  ul {
    list-style: none;
  }
}
.image {
  width: 15rem;
  height: 20rem;
  object-fit: cover;
}

.star {
  color: #ffd700;
}
</style>
