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
.flex {
  display: flex;
  justify-content: space-around;
  place-items: center;
  flex-wrap: wrap;
}
.card {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  max-width: 250px;
  min-height: 250px;
  margin: .5em 0 .5em 1em;
  border-radius: 2em;
  overflow: hidden;
  box-shadow: 5px 8px 10px 4px rgba(0, 0, 0, 0.5);
}
.card h3 {
  margin: 0;
  padding: 0.5em;
  max-width: 300px;
}
.card img {
  max-width: 100%;
  max-height: 350px;
}
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
