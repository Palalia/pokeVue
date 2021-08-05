<template>
<div>
        <content>
        
          <component :is="componenenteactual"> 
            </component>   
       
      </content>  

    </div>  

</template>

<script>

import pokedex from '@/components/pokedex.vue'
import tarjeta from '@/components/tarjeta.vue'


/*import Servicios from '@/components/Servicios.vue'
import Organigrama from '@/components/Organigrama.vue'
import Pooter from '@/components/Footer.vue'
import Objetivo from '@/components/Objetivo.vue'
import Formulario from '@/components/Formulario.vue'
*/
export default {
      name:'app',
  components: {
  pokedex,
  tarjeta,
   },
  data(){
    return{
      componenenteactual:'pokedex',
    }
  },

   methods :{
     seleccionar(nombre){
       this.componenenteactual= nombre
     }
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
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #003b5c;
}
</style>