<template lang="html"> 
    <div>
        <ul>
            <list-item v-for="(character, id) in characters" :character="character" :key="id"></list-item>
        </ul>
    </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
    name: 'character-list',
    props: ['characters'],
    components: {
        "list-item": ListItem
    }
}
</script>

<style>

</style>