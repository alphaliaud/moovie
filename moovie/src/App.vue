<template xmlns:v-on="http://www.w3.org/1999/xhtml">
  <div id="app">
    <div class="container mx-auto">
      <ul class="bg-transparent sm:full md:full lg:full pt-4 pb-4">
        <li class="float-left list-reset inline-block"><img class="w-auto h-16" src="./assets/moovie.svg"></li>
        <button id="show-modal" @click="showModal = true" class="modal-style text-md text-xs rounded-full outline-n float-right hover:bg-green-custom-1 hover:text-white">+ Add movies</button>
        <input type="text" v-model="search" placeholder="Search" class="input-style sm:w-1/5 text-md text-xs float-right outline-n"/>
      </ul>
    </div>

    <ul>
      <movie-item v-for="(movie, index) in movies_search" v-bind:key="movie.title" v-bind:movie="movie" v-on:edit="edit" v-on:remove="remove(index)"></movie-item>
    </ul>

    <p v-if="movie_to_edit">New movie<br />
      Title : <input type="text" v-model="movie_to_edit.title" /><br />
      Year : <input type="text" v-model="movie_to_edit.year" /><br />
      Synopsys : <textarea v-model="movie_to_edit.synopsys"></textarea><br />
      <button v-on:click="save">Save</button></p>

    <div class="card-container container mx-auto max-w-full sm:relative pin-b mb-3 lg:fixed pl-10 pr-10">
      <div class="fixed bg-black-custom-6 pin-b pin-l mb-6 white h-54 w-12 z-1">
        <span class=""></span>
        <span></span>
      </div>
      <div class="fixed bg-black-custom-6 pin-b pin-r mb-6 white h-54 w-12 z-1">
        <span class=""></span>
        <span></span>
      </div>
      <div class="card md:w-1/3 lg:w-1/3 flex">
        <div class="w-1/2 float-left inline-block">
          <div class="card-title mt-4">Le prestige</div>
          <div class="card-title font-extrabold">Sam Nelson</div>
        </div>
        <img class="w-1/2 h-54 rounded-lg float-right inline-block" src="http://fr.web.img3.acsta.net/r_1280_720/pictures/16/12/05/14/10/494493.jpg">
      </div><div class="card md:w-1/3 lg:w-1/3 flex">
      <div class="w-1/2 float-left inline-block">
        <div class="card-title mt-4">Le prestige</div>
        <div class="card-title font-extrabold">Sam Nelson</div>
        <svg class="fill-custom-1 hover:fill-fill w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z"/></svg>
      </div>
      <img class="w-1/2 h-54 rounded-lg float-right inline-block" src="https://www.ecranlarge.com/uploads/image/001/004/black-panther-photo-affiche-7-1004712.jpg">
    </div>
      <div class="card md:w-1/3 lg:w-1/3 flex">
        <div class="w-1/2 float-left inline-block">
          <div class="card-title mt-4">Le prestige</div>
          <div class="card-title font-extrabold">Sam Nelson</div>
        </div>
        <img class="w-1/2 h-54 rounded-lg float-right inline-block" src="http://www.greenroom.fr/wp-content/uploads/2015/06/fight-club-crop.jpg">
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">

  //var app = new Vue({
  export default{

    name: 'app',
    data() {
      return {
        showModal: false,
        message: 'Hello Vue!',
        display: true,
        movie_to_add: {},
        movie_to_edit: null,
        search: "",
        movies :
          [
            {
              title: "L'étrange noël de M. Jack",
              year: 1994,
              synopsys: "Jack Skellington, un épouvantail squelettique surnommé « le Roi des citrouilles » (Pumpkin King en version originale), vit dans la ville d'Halloween. En tant que maître de l'épouvante, Jack occupe ses journées à préparer la prochaine fête d'Halloween."
            },
            {
              title: "Interstellar",
              year: 2014,
              synopsys: "Alors que la Terre se meurt, une équipe d'astronautes franchit un trou de ver apparu près de Saturne conduisant à une autre galaxie, cela dans le but d'explorer un nouveau système stellaire et l'espoir de trouver une nouvelle planète habitable par l'humanité afin de la sauver."
            }
          ]
      }
    },
    methods: {
      newmovie2: function() {
        this.movies.push(this.movie_to_add)
        this.movie_to_add = {}
      },

      edit: function(movie) {
        this.movie_to_edit = movie
      },
      save: function() {
        this.movie_to_edit = null
      },
      remove: function(index) {
        this.movies.splice(index, 1)
      }
    },
    created: function() {
      console.log("Created")
    },
    computed: {
      firstletter: function() {
        return this.message[0]
      },
      movies_search: function() {
        return this.movies.filter(m => m.title.toLowerCase().indexOf(this.search.toLowerCase())!=-1);
      }
    }
  }//)
</script>

<style>

</style>
