<template>
  <div id="app">
    <div class="row">
      <div class="col">
        <h1>
          Tech interview with Staytus
        </h1>
        <h2>
          <a href="mailto:hello@irving.digital?subject=Follow up interview!&body=Let's have a follow up interview!">By Irving Suarez</a>
        </h2>
      </div>
    </div>
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
a{
  color: unset;
}
.row{
  display: flex;
  flex-flow: row wrap;
  justify-content: space-around;
  align-items: stretch;
  //animation: fadeInUp 5s ease-in-out forwards;
}
@keyframes fadeInUp {
    0%{
      opacity: .8;
      transform: translateY(-5em);
      filter: blur(70%);
      }

    100%{
      opacity: 1;
      transform:  translateY(0);
      filter: blur(0%);

    }
  }

</style>
