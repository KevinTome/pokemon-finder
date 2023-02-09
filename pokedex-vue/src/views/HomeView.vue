<script setup lang="ts">

</script>

<template>
  <main>
    <div class="container">
      <div class="form">
        <h3>Search your Pokemon here:</h3>
        <div class="form-input-container">
          <input type="text" placeholder="type any pokemon name" id="pokemon-name">
          <button class="search">
            <i class="fa-solid fa-magnifying-glass input-button"></i>
          </button>
        </div>
      </div>
      <div class="poke-data">
        <div class="poke-title-info">
          <h2 class="hovertext poke-name" data-hover="Name">Name</h2>
          <p class="hovertext type" data-hover="Type">Type</p>  
        </div>
        <div class="poke-sprites">
          <!-- <img src="" alt="Image" class="poke-img"> -->
          <p class="dot"></p>
        </div>
        <div class="poke-stats-info">
          <div class="row-stats">
            <div class="hovertext" data-hover="HP">
              <i class="fa-solid fa-heart"> HP</i>
            </div>
            <div class="hovertext" data-hover="Attack">
              <i class="fa-solid fa-fire-flame-simple"> Atk</i>
            </div>
          </div>
          <div class="row-stats">
            <div class="hovertext" data-hover="Defense">
              <i class="fa-solid fa-shield-halved"> Def</i>
            </div>
            <div class="hovertext" data-hover="Special Attack">
              <i class="fa-solid fa-fire"> SAtk</i>
            </div>
          </div>
          <div class="row-stats">
            <div class="hovertext" data-hover="Special Defense">
              <i class="fa-solid fa-shield"> SDef</i>
            </div>
            <div class="hovertext" data-hover="Speed">
              <i class="fa-solid fa-wind"> Spd</i>
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
  width: 25%;
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
  display: none;
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
.dot {
  height: 10em;
  width: 10em;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
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
