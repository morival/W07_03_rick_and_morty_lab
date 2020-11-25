<template>
<div>
    <h1>Rick and Morty</h1>
  <label for="character_select">Select a Character:</label>
  <select id="character_select" v-model="selectedCharacter">
    <option disabled value="">Select a character</option>
    <option v-for="character in characters" :key="character.id" :value="character">{{character.name}}</option>
  </select>

  <div class="main-container">
    <character-list :characters="characters"></character-list>
    <character-detail :character="selectedCharacter"></character-detail>
  </div>
</div>
</template>

<script>
import CharacterList from './components/CharacterList.vue'
import CharacterDetail from './components/CharacterDetail.vue'
import { eventBus } from './main.js'

export default {
  name: 'App',
  data(){
    return {
    characters:[],
    selectedCharacter: null
    }
  },
  mounted(){
    fetch('https://rickandmortyapi.com/api/character')
    .then(res => res.json())
    .then(characters => this.characters = characters.results)

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character;
    })
  },
  components: {
    "character-list": CharacterList,
    'character-detail': CharacterDetail
    

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
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
