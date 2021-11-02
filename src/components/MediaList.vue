<template>
  <div class="flex">
    <div v-for="media in results" :key="media.id" class="card">
      <img :src="media.Poster" alt="" />
      <h3 class="title">{{ media.Title }}</h3>
      <div class="stats">
        <div class="year">
          <font-awesome-icon class="fa-lg" icon="calendar"></font-awesome-icon>
          {{ media.Year }}
        </div>
        <div class="imdb">
          <a
            :href="'https://www.imdb.com/title/' + media.imdbID"
            target="_blank"
          >
            <font-awesome-icon
              class="fa-2x"
              :icon="['fab', 'imdb']"
            ></font-awesome-icon>
          </a>
        </div>
      </div>

      <div class="type">
        <font-awesome-icon
          v-if="media.Type === 'movie'"
          class="fa-2x"
          icon="film"
        />
        <font-awesome-icon
          v-if="media.Type === 'game'"
          class="fa-2x"
          icon="gamepad"
        />
        <font-awesome-icon
          v-if="media.Type === 'series'"
          class="fa-2x"
          icon="tv"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MediaList",
  props: {
    results: Array,
  },
};
</script>

<style scoped>
.stats {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 3em;
}
.stats > div {
  padding: 0 1em;
}
.type {
  position: absolute;
  top: 1em;
  right: 1em;
  color: rgba(255, 255, 255, 0.5);
}
.type svg,
.year svg {
  margin-right: 0.5em;
}
.imdb a {
  color: black;
}
</style>
