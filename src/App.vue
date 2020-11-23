<template>
  <div id="app">
    <div class="row">
          <review-card/>
          <review-card/>
          <review-card/>
          <review-card/>
          <review-card/>
          <review-card/>
          <review-card/>
    </div>
  </div>
</template>

<script>
import ReviewCard from '@/components/Section/ReviewCard.vue';
import '../src/styles/tailwind.css'

export default {
  name: 'App',
  components: {
    ReviewCard,
  },
}
</script>

<style lang="scss">
html{
  background-color: #CAD4D4;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin:0;
}
.row{
  display: flex;
  flex-flow: row wrap;
  justify-content: space-around;
  align-items: center;
}

</style>
