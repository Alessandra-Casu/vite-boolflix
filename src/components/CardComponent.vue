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
  <ul>
    <li><img :src="cardData.image" :alt="cardData.title" /></li>
    <li>{{ cardData.title }}</li>
    <li>{{ cardData.original_title }}</li>
    <li>
      <LangFlag :iso="cardData.language" :squared="false"></LangFlag>
      <span class="lang-text">{{ cardData.language }}</span>
    </li>
    <li>{{ cardData.rating }}</li>
  </ul>
</template>

<style scoped>
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
