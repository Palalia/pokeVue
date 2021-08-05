
<template>
<div>
    <center>
      <!--barra buscar -->
        <div class="search-container col-md-5 col-sm-5">
          <input type="text" class="form-control" id="search_q" placeholder="buscar pokemon" v-model="aux">
          <button class="btn-search" id="search-btn" v-on:click="getPoke"> 
            <i class="fa fa-search" aria-hidden="true"></i>
          </button>
        </div>  
        <div v-if='mensaje != null'> 
          <div class="col-md-5 col-sm-5 pokemon-card" id="pokemon_details">
           <!--Imagen--> 
            <div class="img-container">
              <img id="update_img" :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${poke.id}.png`" alt="" srcset="">
            </div>
           <!---------->  
            <div class="detail-container">
              <!--nombre-->
              <div class="title-container">
                  <h3 class="name text-center" id="update_name">{{poke.name}}</h3>
                  <hr class="seperator">
                  <div class="stats text-center">
                      <span class="first cp-text col-md-6" id="update_hp">HP 32/32</span>
                      <span class="cp-text col-md-6" id="update_cp">XP 149</span>
                  </div>
              </div>
              <!---------->
              <button class="btn-transfer" >TRANSFER</button>
                <div class="attributes-container">
                  <div class="col attributes-content" style="min-width: 42%;">
                      <p class="cp-text" id="update_type">Electric / Speed</p>
                      <small class="text-muted">Type</small>
                  </div>
                  <div class="col attributes-content">
                    <p class="cp-text" id="update_weight">{{poke.weight}}kg</p>
                    <small class="text-muted">Weight</small>
                  </div>
                  <div class="col attributes-content">
                    <p class="cp-text no-border" id="update_height">{{poke.height}}cm</p>
                    <small class="text-muted">Height</small>
                  </div>
                </div>
            </div>
         </div>
        </div>
    </center>
</div>
</template>
<script> 
import axios from 'axios'
export default {
data(){
    return{
     poke:null,
     mensaje:null,
     aux:null
    }
},
mounted(){},
components:{},
methods:{
    async getPoke(){
        this.mensaje=this.aux;
        console.log("algo");
        const axiosInstance=axios.create({
            headers:{
                "Access-Control-Allow-Origin":"*"
            }
        });
        axiosInstance
        .get("https://pokeapi.co/api/v2/pokemon/"+this.mensaje)
        .then(response=>{
            this.getPokemon=response.data;
            this.poke=response.data;
            this.aux=null;
            console.log(this.poke);
            this.aux=null;
            //this.getMensaje();
        })
        .catch(e=>console.log(e));
    },
    getMensaje(){
      window.location.reload();
    }
}
}
</script>