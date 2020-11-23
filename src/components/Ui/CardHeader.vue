<template>
   <div class="card-header">
      <h4>
        Overall Raiting!
      </h4>
      <p>
        4.2
      </p>
      <span v-for="(rate,index) in overallRaiting" :key="index">
      </span>
        <small>
          65 votes
        </small>
    </div>
</template>

<script>
  export default {
    
  }
</script>

<style lang="sass" scoped>

</style>