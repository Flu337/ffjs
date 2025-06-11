<template>
  <router-link :to="`/details/${movie.id}`" class="movie-card">
    <div v-if="movie.image" class="movie-image-container">
      <img 
        :src="`images/${movie.image}`"
        :alt="movie.title" 
        class="movie-image"
      >
      <div class="movie-overlay">
        <div class="movie-overlay-content">
          <h3>{{ movie.title }}</h3>
          <p class="movie-genre">{{ movie.genre }}</p>
          <p class="movie-short-desc">{{ movie.shortDesc }}</p>
        </div>
      </div>
    </div>
    <div v-else class="movie-image-placeholder">
      {{ movie.title.charAt(0).toUpperCase() }}
      <div class="movie-overlay">
        <div class="movie-overlay-content">
          <h3>{{ movie.title }}</h3>
          <p class="movie-genre">{{ movie.genre }}</p>
          <p class="movie-short-desc">{{ movie.shortDesc }}</p>
        </div>
      </div>
    </div>
  </router-link>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.movie-card {
  display: block;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s, box-shadow 0.3s;
  text-decoration: none;
  color: white;
  background: #333;
  height: 100%;
  position: relative;
}

.movie-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.15);
}

.movie-image-container {
  width: 100%;
  height: 450px;
  overflow: hidden;
  position: relative;
}

.movie-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s;
}

.movie-card:hover .movie-image {
  transform: scale(1.05);
}

.movie-image-placeholder {
  width: 100%;
  height: 450px;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #777;
  font-weight: bold;
  font-size: 48px;
  position: relative;
}

.movie-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  opacity: 0;
  transition: opacity 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  box-sizing: border-box;
}

.movie-card:hover .movie-overlay {
  opacity: 1;
}

.movie-overlay-content {
  text-align: center;
  width: 100%;
}

.movie-overlay-content h3 {
  margin: 0 0 10px 0;
  font-size: 22px;
  white-space: normal;
}

.movie-genre {
  color: #ccc;
  font-size: 16px;
  margin: 0 0 15px 0;
}

.movie-short-desc {
  font-size: 14px;
  line-height: 1.5;
  margin: 0;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 5;
  overflow: hidden;
}
</style>