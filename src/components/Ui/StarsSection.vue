<template>
  <div class="star-section">
          <span class="star" />
          <span class="star" />
          <span class="star" />
          <span class="star" />
          <span class="star" />
            <!-- v-for="(rate,index) in overallRaiting" 
            :key="index"/ -->
        <small>
          <div v-if="overallRaiting === false">
            {{info}}
          </div>
          <div v-else>
            {{votes}} votes
          </div>
        </small>
        </div>
</template>

<script>
  export default {
    name: 'StarsSection',
    props: {
      info: {
        type: [String, Number],
        required: true
      },

      overallRaiting:{
        type: Boolean,
        default: false
      }
    },

    computed: {
      votes() {
        return this.info
      }
    },
    
  }
</script>

<style lang="scss" scoped>

  .star-section{
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex:1;

    .star{
      padding: .45em;
      color: red;
      background-image: url(/star.png);
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }

    small{
      margin-left: 1em;
    }
    
    color:#C1C1C1;
  }
</style>