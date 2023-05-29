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
      <img :src="cardData.image" :alt="cardData.title" />
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
</style>
