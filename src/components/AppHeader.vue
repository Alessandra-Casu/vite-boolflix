<script>
export default {
  data() {
    return {
      searchStr: "",
    };
  },
  methods: {
    onSubmit() {
      console.log(this.searchStr);
      this.$emit("searchRequest", this.searchStr);
    },
  },
};
</script>

<template>
  <form @submit.prevent="onSubmit">
    <span>Boolflix</span>
    <input type="text" v-model="searchStr" />
    <button>CERCA</button>
  </form>
</template>
<style></style>
