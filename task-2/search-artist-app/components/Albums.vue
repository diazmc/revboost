<template>
  <div class="albums-section">
    <div class="album">
      <h3 class="album-title">{{ album.strAlbum }}</h3>
      <p class="album-release-date">Released: {{ album.intYearReleased }}</p>
      <img v-if="album.strAlbumThumb" :src="album.strAlbumThumb" :alt="album.strAlbum" class="album-image">
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  album: Object
});
</script>

<style scoped>
.albums-section {
  text-align: center;
  margin-top: 20px;
}

.albums-title {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

.album {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  margin: 20px auto;
  max-width: 300px;
}

.album-title {
  font-size: 20px;
  color: #333;
}

.album-release-date {
  font-size: 16px;
  color: #666;
  margin-bottom: 20px;
}

.album-image {
  max-width: 100%;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}
</style>
