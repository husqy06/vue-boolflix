<template>
  <header>
    <span id="logo">
      boolflix 
      <span id="logo-components"></span>
    </span>
    <div>
      <input type="text" v-model="inputSearch" @keyup.enter="($emit('searchText', inputSearch)), resetSearch()" placeholder="Cerca film o serie tv">
      <button @click.prevent="($emit('searchText', inputSearch)), resetSearch()">Cerca</button>
    </div>
    
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    msg: String
  },
  data() {
    return {
      inputSearch: "",
    }
  },
  methods: {
    resetSearch() {
      this.inputSearch = "";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/general.scss';
</style>
