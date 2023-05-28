<script>
export default {
  data() {
    return {
      searchStr: "",
    };
  },
};
</script>

<template>
  <form @submit.prevent="this.$emit('searchRequest', searchStr)">
    <span>BoolFlix</span>
    <input type="text" v-model="searchStr" />
    <button>CERCA</button>
  </form>
</template>

<style></style>
