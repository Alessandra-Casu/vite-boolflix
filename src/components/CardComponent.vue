<script>
export default {
  props: {
    cardData: Object,
  },
};
</script>

<template>
  <ul>
    <li>{{ cardData.title }}</li>
    <li>{{ cardData.original_title }}</li>
    <li>{{ cardData.original_language }}</li>
    <li>{{ cardData.vote_average }}</li>
  </ul>
</template>

<style></style>
