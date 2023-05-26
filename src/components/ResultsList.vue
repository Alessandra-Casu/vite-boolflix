<script>
import CardComponent from "./CardComponent.vue";
export default {
  components: { CardComponent },
  props: {
    listTitle: String,
    arrCards: Array,
  },
};
</script>

<template>
  <h2>{{ listTitle }}</h2>
  <CardComponent
    v-for="card in arrCards"
    :key="card.id"
    :cardData="card"
  ></CardComponent>
</template>

<style></style>
