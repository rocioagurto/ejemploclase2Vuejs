<template>
  <div class="container">
    <h1>Series TV</h1>
    <!-- Esta forma se usa cuando no trabajamos con rutas -->
    <button class="btn btn-danger mx-3" @click="seleccion='Series'">Ver Series</button>
    <button class="btn btn-success mx-3" @click="seleccion='Post'">Ver Post</button>
    <button class="btn btn-info mx-3" @click="seleccion='StarWars'">Ver Star-Wars</button>
     <keep-alive>
       <!-- <keep-alive> Mantiene la informacion, no deja que se borre. No deja que la informacion de vuelva a cargar toda nuevamente, si no que la mantiene en pantalla. Tanto keep-alive como component son etiquetas exclusivamente de vue -->
    <component :is="seleccion" :informacion="series"></component>
    </keep-alive>

    <!-- Llamamos al componente series -->
    <!-- <series :informacion="series"></series> -->

    <!-- Llamamos al componente Modal -->
    <modal v-for="(item,index) in series" :key="index" :imagen="item.image.medium" :descrip="item.summary"
      :nombre="item.name" :index="index"></modal>

    <!-- Llamamos al componente Post  -->
    <!-- <post></post> -->

      <!-- Llamamos al componente StarWars-->
   <!-- <star-wars></star-wars> -->

     

  </div>
</template>

<script>
  import axios from 'axios';
  import Series from './components/Series.vue';
  import Modal from './components/Modal.vue';
  import Post from './components/Post.vue';
  import StarWars from './components/StarWars'

  export default {
    name: 'App',

    data() {
      return {
        series: [],
        // Aca se indica series para que inicie en series, podemos poner post y este iniciara en Post o en StarWars, pero puede quedar vacío si asi se requiere
        seleccion:''
      }
    },
    mounted() {
      axios.get('http://api.tvmaze.com/shows')
        .then(response => {
          console.log(response.data);
          this.series = response.data;
        })
        .catch(error => console.log(error))
    },
    components: {
      Series,
      Modal,
      Post,
      StarWars
    },
    beforeDestroy(){
      console.log("por destruir")
    },
    destroyed(){
      console.log("destruido")
    }
  }
</script>

<style>

</style>