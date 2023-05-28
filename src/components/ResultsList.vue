<script>
import CardComponent from "./CardComponent.vue";

export default {
  props: {
    listTitle: String,
    arrCards: Array,
  },
  components: {
    CardComponent,
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
