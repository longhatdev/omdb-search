<template>
  <div>
    <h1>{{ msg }}</h1>
    <input name="query" v-model="searchQuery" type="text" />
    <h3>Results:</h3>
    <MediaList :results="results"></MediaList>
  </div>
</template>

<script>
import MediaList from "@/components/MediaList.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    MediaList,
  },
  data() {
    return {
      apiKey: process.env.VUE_APP_OMDB_API_KEY,
      searchQuery: "",
      results: [],
    };
  },
  methods: {
    getMediasForQuery() {
      const apiUrl = "http://www.omdbapi.com/?apikey=";
      let query = "&s=" + this.searchQuery;
      fetch(apiUrl + this.apiKey + query)
        .then((response) => {
          if (!response.ok) throw new Error(`${response.status}`);
          return response.json();
        })
        .then((response) => {
          this.results = response.Search;
        });
    },
  },
  watch: {
    searchQuery: "getMediasForQuery",
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
