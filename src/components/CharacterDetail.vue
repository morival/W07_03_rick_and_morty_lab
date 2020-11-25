<template lang="html">
  <div v-if="character">
      <h3> {{character.name}} </h3>
      <p>Species: {{character.species}} </p>
      <p>Status: {{character.status}} </p>
      <p>Origin Name: {{character.origin.name}} </p>
      <img class="image" :src="character.image"/>
  </div>
  <div v-else>
      <p>Please choose a character</p>
  </div>
</template>
<script>
export default {
  name: 'character-detail',
  props: ['character']
}
</script>
<style lang="css" scoped>
</style>