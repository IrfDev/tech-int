<template>
  <div class="star-section">
    <star
      v-for="(star,index) in stars" 
      :class="index > stars.length"
      :key="index"
      class="star"
      :overallRaiting="overallRaiting"
      :active="rate <= index ? false : true"
      v-on:click.native="handleRate(index+1)"
    />
  <small v-if="overallRaiting === false">
    {{info}}
  </small>
  <small v-else>
    {{votes}} votes
  </small>
</div>
</template>

<script>
import Star from '@/components/Ui/Star.vue';

  export default {
  name: 'StarsSection',

  data() {
    return {
      rate: 0
    }
  },

  methods: {
    handleRate(rate){
       this.$emit('rate-review', rate)
       this.rate = rate
    },
  },

  components: {
    Star,
  },

    props: {
      info: {
        type: [String, Number],
        required: true
      },

      overallRaiting:{
        type: Boolean,
        default: false
      },

    },

    computed: {
      votes() {
        return this.info
      },

      stars(){
        // I'm using an new Array from Array constructor to simmulate a immutable state
        return new Array(5)
      }
    },
    
  }
</script>

<style lang="scss" scoped>

  .star-section{
    display: flex;
    align-items: center;
    flex:1;
    small{
      margin-left: .5em;
    }
    
    color:#C1C1C1;
  }
</style>