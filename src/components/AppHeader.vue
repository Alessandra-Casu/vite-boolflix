<script>
export default {
  data() {
    return {
      searchStr: "",
    };
  },
  methods: {
    onSubmit() {
      this.$emit("searchRequest", this.searchStr);
    },
  },
};
</script>

<template>
  <header>
    <div class="container">
      <form class="sub-container" @submit.prevent="onSubmit">
        <span>BOOLFLIX</span>
        <div class="right">
          <input
            type="text"
            v-model="searchStr"
            placeholder="Inserisci il tuo titolo"
          />
          <button class="btn">CERCA</button>
        </div>
      </form>
    </div>
  </header>
</template>
<style lang="scss" scoped>
header {
  background-color: black;
  color: white;
  height: 5rem;
  padding: 1.2rem;
  span {
    font-size: 4rem;
    font-weight: 900;
    color: red;
    padding-right: 2rem;
  }
  input {
    height: 2rem;
    width: 25rem;
    border-radius: 1rem;
    padding: 0.5rem;
  }
  .btn {
    width: 5rem;
    height: 2rem;
    background-color: red;
    color: black;
    border: 1px solid black;
    border-radius: 1rem;
    margin-left: 2rem;
  }
}
.container {
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.sub-container {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
