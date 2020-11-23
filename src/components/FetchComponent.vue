<template>
  <div class="fetch-component">
    <div class="row">
      <div v-if="asyncStatus ==='loading'" class="column">
        Loading...
      </div>
      <div v-if="asyncStatus ==='resolve'" class="column">
        <pre>
          {{JSON.stringify(apiData, null, 2)}}
        </pre>
      </div>
      <div v-if="asyncStatus ==='error'" class="column">
        <pre>
          {{JSON.stringify(apiData, null, 3)}}
        </pre>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'FetchComponent',

  data() {
    return {
      asyncStatus: '',
      apiData: {}
    }
  },

  mounted () {
    this.fetchApi();
  },

  methods: {
    async fetchApi() {
      this.asyncStatus = 'loading'

    try {
      let data = await fetch('https://randomuser.me/api');

      let parseData = await data.json();

      this.asyncStatus = 'resolve'

      this.apiData = parseData

    } catch (error) {
      this.asyncStatus = 'error'
      this.apiData = {
        error,
        message: error.message
      }
    }

      

    }
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



</style>
