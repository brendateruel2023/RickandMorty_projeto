<script setup>
import { onMounted, reactive, ref } from 'vue';
import ListCharacters from '../components/ListCharacters.vue';

let characters = reactive(ref());

onMounted(() => {
  fetch("https://rickandmortyapi.com/api/character")
    .then(response => response.json())
    .then(response => {
      characters.value = response.results;
      console.log(characters.value); 
    });
});
</script>

<template>
  <main class="d-flex align-items-end justify-content-center" style="min-height: 100vh;">
    <div class="col-sm-12 col-md-6">
      <div class="card" style="width: 100%;">
        <div class="card-body row">
          <ListCharacters 
            v-for="character in characters"
            :key="character.name"
            :name="character.name"
            :image="character.image"
            :status="character.status"
            :species="character.species"
            :gender="character.gender"
            :location="character.location"
            :episodeCount="character.episode.length" 
          />
        </div>
      </div>
    </div>
  </main>
</template>

<style>
  main {
    flex-grow: 1;
    display: flex;
    align-items: flex-end;
    justify-content: center;
  }
</style>


