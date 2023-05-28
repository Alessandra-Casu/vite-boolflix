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
      <li>{{ cardData.rating }}</li>
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
