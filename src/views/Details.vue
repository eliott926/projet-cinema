<template>


  <div class="details">
    <h1> {{film.titre}}</h1>
    <br>
    <br>
    <h1>Details du film</h1>
    <br>
    <p>Résumé: {{films.overview}}</p>
    <br>

    <div class="content">

      <br>

      <p> Note: {{films.vote_average}}/10</p>



      <h1> Acteurs </h1>

      <br>


      </div>


    </div>
  <
</template>

<script>
import axios from 'axios'

export default {
  name: 'Details',
  data(){
    return{
      film : [],
      films : [],
      cast: [],

      unDetail: '',
      api_key: '3f2e73f99471592447bae321c22cd045'
    }
  },


  created(){
    this.film = {
      id: this.$route.query.id,
      titre: this.$route.query.titre

    }
    this.recherche();
    this.recherche1();
  },

  methods: {
    async recherche(){
      const response = await axios.get('https://api.themoviedb.org/3/movie/' + this.film.id + '?api_key=' + this.api_key + "&language=fr");
      // https://api.themoviedb.org/3/movie/335983?api_key=3f2e73f99471592447bae321c22cd045&language=fr
      this.films = await response.data;
    },
    async recherche1(){
      const response = await axios.get('https://api.themoviedb.org/3/movie/' + this.film.id + '/credits?api_key=' + this.api_key + "&language=fr");
      // https://api.themoviedb.org/3/movie/335983/credits?api_key=3f2e73f99471592447bae321c22cd045&language=fr
      this.cast = await response.data;
    },

  }
}
</script>


<style>

.content h1, .content h2, .content h3, .content h4, .content h5, .content h6 {
  color: #ffffff;
  font-size: 100%;
  font-weight: normal;
  line-height: 1.125;
}

.card{
  background-color: dimgrey;
}

.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  border-radius: 5px; /* 5px rounded corners */
}

/* Add rounded corners to the top left and the top right corner of the image */
img {
  width: 200px;
  border-radius: 5px 5px 5px 5px;
}
</style>

