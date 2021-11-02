<template>
  <div class="home">
    <HelloWorld msg="Search for a movie, series or anything..." />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
};
</script>

<style lang="postcss">
.home {
  padding: 1em;
}
</style>
