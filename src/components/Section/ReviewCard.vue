<template>
  <div :class="{dark: isRated}" v-if="asyncStatus === 'resolve'" class="review-card flex flex-col items-center">
    <div class="card-header flex items-center text-left justify-between">
      <div class="title">
        <h4>
          Overall raiting
        </h4>
      </div>
      <div class="raiting">
        <p>
          4.2
        </p>
      <stars-section
        :overallRaiting="true"
        :info="votes"
        v-on:rate-review="handleRate"
      />
      </div>
      <div class="plus">
        +
      </div>
    </div>
    <div class="card-body">
      <div class="card-information">
          <img
            class="avatarr"
            :src="apiData.picture.thumbnail"
            alt="avatar"
          >
          <div class="review-info">
            <h4>
                {{`${apiData.name.first} ${apiData.name.last}`}}
            </h4>
            <stars-section
              info="6 days ago"
            />
          </div>
        </div>
      <div class="card-review">
        <p>
          {{
            `E-mail: ${apiData.email}
            Phone: ${apiData.phone}
            `
          }}
        </p>
        <small>
          from 
          {{
            `
              ${apiData.dob.age} -
              ${apiData.dob.date} 
            `
          }}
        </small>
      </div>
    </div>
    
  </div>

  <div v-else-if="asyncStatus ==='loading'" class="loading">
    <h1></h1>
  </div>

  <div v-else>
    <pre>
      {{
        JSON.stringify(apiData, null, 2)
      }}
    </pre>
  </div>

</template>

<script>
import StarsSection from '@/components/Ui/StarsSection.vue';
// When you click on the stars, change the background color. { JUST FOR THE SECOND STAR COMPONENT }

  export default {
    name: 'ReviewCard',

    components: {
      StarsSection,
    },

  data() {
    return {
      asyncStatus: '',
      apiData: {},
      isRated: false,
      rate: 0
    }
  },

  mounted () {
    this.fetchApi();
  },

  computed: {
      votes() {
        return this.apiData ? this.apiData.dob.age + this.rate : ''
      },
    },

  methods: {
     handleRate(rate){
      this.isRated = true
      this.rate = rate
    },


    async fetchApi() {
      this.asyncStatus = 'loading'

      try {
        let data = await fetch('https://randomuser.me/api');

        let {results: parseData} = await data.json();

        this.apiData = parseData[0]
        this.asyncStatus = 'resolve'


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

<style lang="scss" scoped>
.loading{
  width: 20em;
}
 
.review-card{
  animation: fadeInUp .4s ease-out forwards;
  margin: 1em 0;
  background-color: #fff;
  // Fonts
  font-family: Montserrat;
  border-radius: 25px;
  width: 20em;
  &>*{
    animation: fadeInDown .5s ease-in forwards;
  }

    transition: all ease-in .5s;
  &:hover{
    transition: all ease-out .4s;
    box-shadow: 1px 4px 8px rgba(0, 0, 0, 0.356);
  }

  .card-header{
    display: flex; 
    align-items: center;
    text-align: left;
    flex-flow: row wrap;
    justify-content: space-between;
    border-bottom: #D4DDDD .3px solid;
    padding: 7% 10%;

    .title{
      flex-basis: 100%;
      font-weight: 700;
      h4{
        margin-block-start:.5em;
        margin-block-end: 0;  
      }
    }
  

    p{
      color: #40918C;
      font-weight: 400;
      margin-right: 1em;
    }

    .raiting{
      display: flex;
      align-items:center;
      flex-flow: row wrap;
      justify-content: space-around;
      flex-basis: 70%;
    }

    .plus{
      padding: 1em 1.2em;
      background-image: linear-gradient(
        184deg, rgba(243,246,246,1) 0%, rgba(243,246,246,1) 100%
      );
      color:#2F4051!important;
      font-weight: 900;
      border-radius: 12px;
      background-size: 100%; 
      background-position: center center;
      background-repeat: no-repeat;
    }
  }

  .card-body{
    padding: 11%;
    padding-top: 7%;

    .card-information{
      display: flex;
      align-items: center;
      align-content: center;
      .avatarr{
        height: 3em;
        margin: 5% 5% 5% 0;
        width: auto;
        border-radius: 15px;
      }

    }

    .card-review{
      text-align: left;
      font-weight: 400;
        p{
          text-overflow: ellipsis;
          width: 100%;
          overflow: hidden;
        }
    }
  }

  .review-info{
    h4{
      text-align: left;
      margin:0;
      margin-block-start: none;
      margin-block-end:.5em;
    }
  }

    &.dark{
      transition: all ease-in-out .5s;
      background-color: black;
      color: #eee!important;
    }
}
@keyframes fadeInUp {
    0%{
      opacity: .5;
      filter: blur(70%);
      transform: translateY(2em);
      }

    100%{
      opacity: 1;
      filter: blur(0%);

    }

  }

@keyframes fadeInDown {
    0%{
      opacity: .5;
      filter: blur(70%);
      transform: translateY(-1em);
      }

    100%{
      opacity: 1;
      filter: blur(0%);

    }
  }
</style>