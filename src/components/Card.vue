<template>
  <section>

    <section class="card-container">
      <span class="card-section-title">film</span>

      <div class="flip-card" v-for="(movie, index) in movieArray" :key="index">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <img :src="'https://image.tmdb.org/t/p/original/'+ movie.poster_path" :alt="movie.title">
          </div>
          <div class="flip-card-back">
            <span>Titolo: {{ movie.title }}</span>
            <span>Titolo originale: {{ movie.original_title }}</span>
            <span>Lingua: {{ movie.original_language }}</span>
            <!--<img :src="require('../assets/flagImg/' + movie.original_language + '.png')" :alt="movie.original_language"> -->
            <!-- se metto la bandiera cosi il sito non refresha quando faccio una ricerca, non ho capito perche -->
            <span>Voto:
              <span class="starVote" v-for="n in getFullStar(movie.vote_average)" :key="n"><i class="fas fa-star"></i></span>
              <span class="starVote" v-for="j in getEmptyStar(movie.vote_average)" :key="j"><i class="far fa-star"></i></span>
            </span>
          </div>
        </div>
      </div>
    </section>

    <section class="card-container">
      <span class="card-section-title">serie tv</span>

      <div class="flip-card" v-for="(serie, index) in serieArray" :key="index">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <img :src="'https://image.tmdb.org/t/p/original/'+ serie.poster_path" :alt="serie.name">
          </div>
          <div class="flip-card-back">
            <span>Nome: {{ serie.name }}</span>
            <span>Nome originale: {{ serie.original_name }}</span>
            <span>Lingua: {{ serie.original_language }}</span>
            <span>Voto: 
              <span class="starVote" v-for="d in getFullStar(serie.vote_average)" :key="d"><i class="fas fa-star"></i></span>     
              <span class="starVote" v-for="g in getEmptyStar(serie.vote_average)" :key="g"><i class="far fa-star"></i></span>    
            </span>
          </div>
        </div>
      </div>
    </section>
      
    
 </section>
</template>

<script>
export default {
  name: 'Card',
  props: ['movieArray', 'serieArray'],
  methods: {
    getFullStar(value) {
      let numStar = Math.round(value / 2);
      return numStar
   },
   getEmptyStar(value) {
     let numStar  = Math.round(value / 2);
     let emptyStar = 5 - numStar;
     return emptyStar
   }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/general.scss';
</style>
