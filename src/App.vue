<template>
  <div id="app">  
    <Header   @search='searchNeedledFilms' />
    <Main :needle='needle' :filmGroup='filmGroup' :TVSeriesGroup='TVSeriesGroup'/>    
    
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data: function(){
    return{
      filmGroup:[],
      TVSeriesGroup:[],
      needle: '',
      URLFilm: 'https://api.themoviedb.org/3/search/movie',
      URLTVSeries: 'https://api.themoviedb.org/3/search/tv',
      apiKey: '3b011c5c1e17392d4dbd111e35c9ab78'
     
    }
  },
  methods: {

    searchNeedledFilms: function(needle){
        if(needle.length > 0){
            axios.get(this.URLFilm, {
        params: {
          api_key: this.apiKey,
          query: needle
        }
      }).then((response) =>{
        this.filmGroup = [...response.data.results]
        console.log(this.filmGroup);
      });
      axios.get(this.URLTVSeries, {
        params: {
          api_key: this.apiKey,
          query: needle
        }
      }).then((response) =>{
        this.TVSeriesGroup = [...response.data.results];
        console.log(this.TVSeriesGroup)
      })
        }
        this.needle = needle;
    }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';


</style>
