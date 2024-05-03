<script setup>
  const character = defineProps(["name", "image", "status", "species", "gender", "location", "episodeCount"]);

  const imageUrl = `https://rickandmortyapi.com/api/character/avatar/${character.image.split('/').pop()}`;
</script>

<template>
  <div class="col-md-4">
    <div class="card mb-3 text-center d-flex align-items-center justify-content-center" style="min-height: 100%">
      <img :src="imageUrl" height="250" alt="..." class="card-img-top">
      <div class="card-body">
        <h5 class="card-title">{{ character.name }}</h5>
        <p>Status: {{ character.status }}</p>
        <p>Espécie: {{ character.species }}</p>
        <p>Gênero: {{ character.gender }}</p>
        <p>Localização: {{ character.location.name }}</p>
        <p>Número de episódios: {{ character.episodeCount }}</p>
      </div>
    </div>
  </div>
</template>

<style>
</style>


