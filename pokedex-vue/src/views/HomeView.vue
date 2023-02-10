<script lang="ts">
  import axios from 'axios';
  
  export default{
    data(){
      return{
        isActive: true,
        inputInfo: '',
        pokemonData: '',
        nameInfo: 'Name',
        typeInfo: 'Type',
        imgSrc: '',
        hpStats: 'HP',
        atkStats: 'Atk',
        defStats: 'Def',
        satkStats: 'SAtk',
        sdefStats: 'SDef',
        spdStats: 'Spd'
      };
    },
    methods: {
      search(e: string) {
        axios.get(`https://pokeapi.co/api/v2/pokemon/${this.inputInfo.toLowerCase()}`)
        .then((response) => {
          this.pokemonData = response.data;

          this.isActive = false;
          this.nameInfo = this.pokemonData.name;
          this.typeInfo = this.pokemonData.types[0].type.name; //[ERR]more than one type
          this.imgSrc = this.pokemonData.sprites.front_default;
          this.hpStats = this.pokemonData.stats[0].base_stat;
          this.atkStats = this.pokemonData.stats[1].base_stat;
          this.defStats = this.pokemonData.stats[2].base_stat;
          this.satkStats = this.pokemonData.stats[3].base_stat;
          this.sdefStats = this.pokemonData.stats[4].base_stat;
          this.spdStats = this.pokemonData.stats[5].base_stat;
        })
        .catch((err) => {
          alert("There's not a Pokemon with that name, try again!")
        });
      }
    }
  };

</script>

<template>
  <main>
    <div class="container">
      <div class="form">
        <h3>Search your Pokemon here:</h3>
        <div class="form-input-container">
          <input type="text" v-model="inputInfo" placeholder="type any pokemon name" id="pokemon-name">
          <button class="search" @click="search(inputInfo)">
            <i class="fa-solid fa-magnifying-glass input-button"></i>
          </button>
        </div>
      </div>
      <div v-bind:class="{hide: isActive}" class="poke-data">
        <div class="poke-title-info">
          <h2 class="hovertext poke-name" data-hover="Name">{{ nameInfo }}</h2>
          <p class="hovertext type" data-hover="Type">{{ typeInfo }}</p>  
        </div>
        <div class="poke-sprites">
          <img :src="imgSrc" alt="Image" class="poke-img">
        </div>
        <div class="poke-stats-info">
          <div class="row-stats">
            <div class="hovertext" data-hover="HP">
              <i class="fa-solid fa-heart" id="poke-hp"> {{ hpStats }}</i>
            </div>
            <div class="hovertext" data-hover="Attack">
              <i class="fa-solid fa-fire-flame-simple" id="poke-atk"> {{ atkStats }}</i>
            </div>
          </div>
          <div class="row-stats">
            <div class="hovertext" data-hover="Defense">
              <i class="fa-solid fa-shield-halved" id="poke-def"> {{ defStats }}</i>
            </div>
            <div class="hovertext" data-hover="Special Attack">
              <i class="fa-solid fa-fire" id="poke-satk"> {{ satkStats }}</i>
            </div>
          </div>
          <div class="row-stats">
            <div class="hovertext" data-hover="Special Defense">
              <i class="fa-solid fa-shield" id="poke-sdef"> {{ sdefStats }}</i>
            </div>
            <div class="hovertext" data-hover="Speed">
              <i class="fa-solid fa-wind" id="poke-spd"> {{ spdStats }}</i>
            </div>
            
          </div>
        </div>
      </div>
    </div>    
  </main>
</template>

<style scoped>

main{
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #5a07a8;
  background: linear-gradient(180deg, rgba(90,7,168,1) 0%, rgba(0,0,0,1) 100%);
}
.container{
  background-color: blueviolet;
  width: 90%;
  max-width: 450px;
  /* height: 45%; */
  aspect-ratio: 1;
  border-radius: 5%;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.form{
  width: 100%;
  margin: 2em 0;
  padding: 1em 0;
  background-color: whitesmoke;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.form h3{
  font-size: 1.5em;
  padding: 1em;
  font-weight: 900;
}
.form-input-container{
  display: flex;
  align-items: center;
  width: 90%;
}
#pokemon-name{
  padding: .8rem;
  border: none;
  flex: 1;
  border-radius: 1em;
}
.search{
  min-width: 4em;
  height: 100%;
  padding: 0.8rem;
  margin-left: 8px;
  background-color: #5a07a8;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 1em;
}
.hide{
  display: none !important;
}
.poke-data{
  display: flex;
  justify-content: center;
  flex-direction: column;
  width: 90%;
}
.poke-title-info{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-evenly;
}
.poke-name{
  text-transform: capitalize;
  font-size: 2em;
}
.type{
  font-size: 1.2em;
  color: antiquewhite;
}
.poke-sprites{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1em;
}
.poke-img{
  width: 10em;
  border-radius: 50%;
  border: .1em dashed black;
}
.poke-stats-info{
  height: 100%;
  display: flex;
  flex-direction: column;
  gap: 3em;
  margin: 1em 0;
}
.row-stats{
  display: flex;
  justify-content: space-around;
  padding: 1em;
}
.hovertext {
  position: relative;
}
.hovertext:before {
  content: attr(data-hover);
  visibility: hidden;
  opacity: 0;
  width: 140px;
  background-color: black;
  color: #fff;
  text-align: center;
  border-radius: 5px;
  padding: 5px 0;
  transition: opacity 1s ease-in-out;

  position: absolute;
  z-index: 1;
  left: 0;
  top: 110%;
}
.hovertext:hover:before {
  opacity: 1;
  visibility: visible;
}
</style>
