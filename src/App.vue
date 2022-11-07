<template>
  <img alt="PokPlant" src="">
  <HelloWorld msg="¡Bienvenido!...¿Que planta deseas buscar?"/>
  <Header class="header">
    <label for="">
      Planta:
      <input 
      type="text" name="" 
      v-model=" plantaName"
      >
      <button 
      class="SearchButton"
      @click="Searchplanta"
      >
        Search planta
      </button>
    </label>
  </Header>
  
  <main 
  class="main"
  v-if="Objet.entries(plantaData).length > 0"
  >
    <section class="PlantaCard">
      <div class="nameImage">
        <h1 class="PlantaName">{{plantaData.name}}</h1>
        <img src="" alt="ImgPlanta">
      </div>
      <ul class="Nombre Cientifico">
        <h2>Nombre Cientifico:</h2>
        <li>
          <span>Nombre Cientifico</span>
        </li>
      </ul>
      <ul class="type">
        <h2>Type:</h2>
        <li>
          <span>Tipo Planta</span>
        </li>
      </ul>
      <ul class="Caracteristicas">
        <h2>Caracteristicas:</h2>
        <li>
          <span>Caracteristicas</span>
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
import { plantaapi } from './api/plantaapi';
export default {
  name:"App",
  data() {
    return {
      plantaData:{},
      plantaName:"",
      plantaNameCientifico:"",
      plantaType:"",
      plantaCaracteristicas:"",
    }
  },
  methods: {
    async Searchplanta() {
      try{
        const plantaToFind = await fetch (`${plantaapi}/${this.plantaName}`)
        const planta = await plantaToFind.json()
        this.plantaData = planta
        console.log(planta)
        return planta
      } catch (error){
        alert('planta was not found')
      }
    }
  }
}


</script>

<style>

</style>
