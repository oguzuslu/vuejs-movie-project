<template>
  <div id="app">

      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
  <a class="navbar-brand"  href="#"><img src=" ../src/assets/logo.png"/></a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item ">
        <a class="nav-link" href="#">HOME </a>
      </li>
      <li class="nav-item active">
        <a class="nav-link" href="#">POPULAR</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">TOP RATED</a>
      </li>
     
    </ul>
    
  </div>
  </div>
</nav>


    <div  class="container mt-5" >


 <div class="row"  >
<ul>
  <li v-for="post in movie" v-bind:key="post" :post="post" >
     <b-card 
    overlay 
    :img-src  = "'//image.tmdb.org/t/p/w342'+post.poster_path" 
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"

  >
    <b-card-text >
    <div>
    <ul class="card-index" center>
      <li class="card-title"> {{post.title}}</li>
      <li><span class="card-subtitle">Beğeni :</span> {{post.vote_count}}</li>
      <li><span class="card-subtitle">Çıkış Tarihi :</span> {{post.release_date}}</li>
      <li class="scroll"><span class="card-subtitle">Özet :</span> {{post.overview}}</li>
    </ul>
    </div>
    </b-card-text>

 <template v-slot:footer>
       <li>IMDB : {{post.vote_average}}</li>
      </template>
 
  </b-card>
  </li>
</ul>

   </div>
</div>
<footer class="page-footer font-small blue">

  
  <div class="footer-copyright text-center py-3">© 2020 Copyright:
    <a href="#"> movietime.com</a>
  </div>


</footer>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      movie: {},
      
      
      
    }
  },
  components: {
  },
  methods:{
    fetchSomeData(){
      fetch('https://api.themoviedb.org/3/movie/popular?api_key=511b327e61b94758d88f07f2a14a39d7&language=en-US&page=1', {
        method: 'GET'
      }).then((resp)=> {
       return resp.json();
     }).then((obj)=>{
       console.log(obj);
      this.movie = obj.results;
      
    })
  }
  
  },
  
  created(){
    this.fetchSomeData()
    
   
    
  }

}
</script>

<style lang="scss">

@import "./styles/custom.scss";
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:$primary;
  
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}


.mb-2{
    max-width: 15rem!important;
}

</style>
