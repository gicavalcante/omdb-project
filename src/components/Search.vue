<template>
   <div class='search'>
  <h1>Search</h1>
  <input type='text' v-model='query' @keyup='getResult(query)'>
  <div v-for='result in results' :key='result.id'>
   <p>{{result.Title}}</p>
   <img v-bind:src="result.Poster" width='100px'>
  </div>
 </div>
 </template>

<script>
import axios from 'axios'
export default {
 name: 'search',
 data () {
 return {
  query: '',
  results:[]
}
 },
 methods: {
  getResult(query) {
      axios.get(`http://www.omdbapi.com/?apikey=45ebdd49&t=${query}`).then(response => { this.results.push(response.data) })
   console.log(this.results)
  }
 }
}

</script>
