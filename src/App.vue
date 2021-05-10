<template>
  <div id="app">

    <Nav></Nav>
    <div>{{message}}</div>
    <div class="container">
       <div class="row">
         <!-- key here is important -->
       <!-- <Card v-for="tv in tvobj" :key=tv.id v-bind:obj=tv class="col  d-flex align-items-stretch"></Card> -->
        <Card v-for="movie in movies" :key=movie.id v-bind:obj=movie class="col"></Card>
    </div>
    </div>
   
     
   
  </div>
</template>

<script>
  import Card from './components/Card.vue'
  import Nav from './components/Nav.vue'
  import axios from 'axios'

  export default {
    name: 'App',
    components: {
      Card,
      Nav
    },
    data()
    {
      return{
        message: "mymessage",
        tvobj: [
                    {id:1, title:"matrix", overview:"descritipn", poster_path:"matrix.jpg"},
                    {id:2, title: "top gun", desc: "2nd desc", poster_path:"topgun.jpg"}
                ],
        movies:[]

        
      }
    },
    mounted(){
      axios.get("https://api.themoviedb.org/3/movie/now_playing?api_key=70ef7c62eee1244489c96681175a2a0f&language=en-US&page=1")
      .then(  (response) =>
      {
        console.log(response)
        this.movies = response.data.results
      })
      
    }
  } 
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>