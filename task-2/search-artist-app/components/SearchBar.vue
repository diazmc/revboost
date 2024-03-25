<template>
  <div class="search-container">
    <form @submit.prevent="searchArtist" class="search-form">
      <input 
        v-model="searchQuery" 
        type="text" 
        placeholder="Search for an artist..." 
        @focus="clearSearchQuery"
        class="search-input"
      />
      <button type="submit" class="search-button">Search</button>
    </form>

    <div v-if="error" class="error-message">{{ error }}</div>

    <div v-if="artist" class="artist-info">
      <h2 class="artist-name">{{ artist.strArtist }}</h2>
      <img v-if="artist.strArtistThumb" :src="artist.strArtistThumb" :alt="`${artist.strArtist} image`" class="artist-image">
      <!-- Fetch artist's albums -->
      <button @click="searchAlbums(artist.strArtist)" class="album-button">Show Albums</button>
    </div>
    <div v-if="loading" class="loading-message">Loading...</div>

    <!-- Display albums if any -->
    <div v-if="albums.length" class="albums-container">
      <h2 class="albums-title">Albums:</h2>
      <Albums v-for="album in albums" :key="album.idAlbum" :album="album" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import axios from 'axios';

const searchQuery = ref('');
const artist = ref(null);
const error = ref(null);
const loading = ref(false);


async function searchArtist() {
  loading.value = true;
  artist.value = null;
  error.value = null;
  albums.value = [];
  try {
    // Replace spaces with underscores
    const formattedQuery = searchQuery.value.replace(/\s+/g, '_').toLowerCase();

    // Only works with 'coldplay'
    const response = await axios.get(`https://www.theaudiodb.com/api/v1/json/2/search.php?`, {
      params: {
        s: formattedQuery
      }
    });

    if (response.data.artists && response.data.artists.length > 0) {
    artist.value = response.data.artists[0]; // Assign the first artist found
    } else {
      artist.value = null; // No artists found, set artist to null
      error.value = `No results found for "${formattedQuery}. Try 'coldplay'`; 
    } 
  } catch (err) {
    error.value = err.message;
    artist.value = null;
  } finally {
    loading.value = false;
  }
}


const albums = ref([]); // To store the albums

async function searchAlbums(artistName) {
  loading.value = true;
  error.value = null;
  try {
    // const response = await axios.get(`https://www.theaudiodb.com/api/v1/json/2/album.php?`, {
    //   params: {
    //     s: artistName // Use the artist'name to fetch albums
    //   }
    // });
   
    // Only shows Daft Punk's albums
    const response = await axios.get('https://www.theaudiodb.com/api/v1/json/2/searchalbum.php?s=daft_punk');
    albums.value = response.data.album || [];
  } catch (err) {
    error.value = err.message;
    albums.value = []; // Reset albums on error
  } finally {
    loading.value = false;
  }
}

function clearSearchQuery() {
  error.value = ''; // Clear error message below search bar
}

</script>

<style scoped>
.search-container {
  max-width: 600px;
  margin: auto;
  padding: 20px;
  font-family: 'Arial', sans-serif;
}

.search-form {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.search-input {
  flex-grow: 1;
  padding: 10px;
  border: 2px solid #ddd;
  border-radius: 4px;
}

.search-button {
  padding: 10px 20px;
  background-color: #333;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.search-button:hover {
  background-color: #555;
}

.artist-info, .albums-container {
  text-align: center;
}

.artist-name {
  margin: 20px 0;
  font-size: 24px;
}

.artist-image {
  display: block;
  width: 300px; /* Adjust the width as needed to match album image size */
  height: auto;
  border-radius: 4px;
  margin: 10px auto;
}

.album-button {
  background-color: transparent;
  border: 2px solid #333;
  border-radius: 4px;
  padding: 8px 16px;
  cursor: pointer;
  font-size: 16px;
}

.album-button:hover {
  background-color: #f5f5f5;
}

.error-message, .loading-message {
  text-align: center;
  margin-top: 20px;
}
</style>