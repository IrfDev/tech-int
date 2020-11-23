<template>
  <div id="app">
    <div class="row">
      <div class="column">
          <review-card/>
      </div>
    </div>
  </div>
</template>

<script>
import ReviewCard from '@/components/Section/ReviewCard.vue';

export default {
  name: 'App',
  components: {
    ReviewCard,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.row{
  display: flex;
}

</style>
