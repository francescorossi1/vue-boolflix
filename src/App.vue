<template>
  <div>
    <MainHeader @text-searched="searchMovies"/>
    <div id="movies-list">
      <ul v-for="result in results" :key="result.id">
        <li><strong>Titolo: </strong>{{result.title}}</li>
        <li><strong>Titolo Originale: </strong>{{result.original_title}}</li>
        <li><strong>Lingua Originale: </strong>{{result.original_language}}</li>
        <li><strong>Voto: </strong>{{result.vote_average}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import MainHeader from './components/MainHeader.vue'


export default {
  name: 'App',
  components: {
    MainHeader
},
  data() {
    return {
      searchText: '',
      baseUri: 'https://api.themoviedb.org/3',
      apiKey: '8879e538b99f81d0c88c4cdd01f5dc49',
      results: []
    }
  }, computed: {
    
  },
  methods: {
    setSearchText(value){
      this.searchText = value
    },
    searchMovies(value) {
      this.setSearchText(value)
      if (!this.searchText) return
      axios.get(`${this.baseUri}/search/movie/?api_key=${this.apiKey}&language=it&query=${this.searchText}`)
        .then((res) => {
          this.results = res.data.results.map((result)=>{
            const {id, title, original_title, original_language, vote_average} = result
            return {id, title, original_title, original_language, vote_average}
          })
        })
    }
  }
}
</script>

<style lang="scss">
</style>
