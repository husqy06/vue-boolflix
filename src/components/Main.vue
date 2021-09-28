<template>
  <main>
    <Card :movieArray="movieArray" :serieArray="serieArray"/>
  </main>
</template>

<script>
import Card from './Card.vue';

export default {
  name: 'Main',
  components : {
    Card
  },
  props: ['movieArray', 'serieArray'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/general.scss';
</style>
