<template>
  <div class="home">
    <br>
    <h1>Lista de Juegos disponibles</h1>
    <br>
    <div v-for="(juego,index) in juegos" :key="index">
      <ListadeJuegos 
      :games="juegos"
      @viewAdmin="adminView(juego.name)">
      </ListadeJuegos>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import ListadeJuegos from '@/components/ListadeJuegos.vue'

export default {
  name: 'home-view',
  data: function () {
    return {
      key: '5dbe2557b132492aba115b0339bc0300',
      juegos: [],
      opiniones: [],
      nombre: '',
      opinion: '',

    }
  },
  components: {
    ListadeJuegos
  },
  methods: {
    obtenerDatos() {
      axios.get(`https://api.rawg.io/api/games?dates=2019-09-01%2C2019-09-30&key=1b401d34f5474ded8af3451186dd25f6&page=2&platforms=20%2C1%2C7/`)
        .then((resp) => {
          console.log(resp.data.results);
          this.juegos = resp.data.results
        })
        
    },
/*     adminView(name){
      //alert(name);
      this.$router.push({name: 'admin', params: {id: name}});
    }, */
/*     adminView(name){
      alert(name);
      this.$router.push('/administracion/');
    }   */

  },
  created(){
    this.obtenerDatos()
  }



}
</script>
