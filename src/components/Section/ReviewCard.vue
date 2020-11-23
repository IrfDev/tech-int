<template>
  <div class="review-card">
    <div class="card-header">
      <!-- <h4>
        Overall Raiting!
      </h4> -->

    <div class="rating">
      <p>
          4.2
        </p>
        <div>
        <small>
          65 votes
        </small>
      </div>


    </div>
      <div class="star-section">
     
      <span class="star" />
      <span class="star" />
      <span class="star" />
      <span class="star" />
      <span class="star" />
        <!-- v-for="(rate,index) in overallRaiting" 
        :key="index"/ -->
    </div>

      <div class="plus"/>
    </div>
    <div class="card-body">
      <div class="card-information">
          <img class="avatar" src="/avatar.png" alt="avatar">
          <div class="review-info">
            <h5>
                Philip Martin
            </h5>
            <div class="star-section">
             <span
              class="star" 
             />
             <span
              class="star" 
             />
             <span
              class="star" 
             />
             <span
              class="star" 
             />
             <span
              class="star" 
             />
             <!-- v-for="(rate, index) in individualRaiting" :key="index" -->
            <small>
              6 days ago
            </small>
            </div>
          </div>
        </div>
      <div class="card-review">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum.
        </p>
        <small>
          from Facebook
        </small>
      </div>
    </div>
  </div>
</template>

<script>
// When you click on the stars, change the background color. { JUST FOR THE SECOND STAR COMPONENT }

/* - rating - id - picture - use thumbnail - description - email with phone number - from - dob and age 
De Roy Francis Staytus para Todos: (9:23 a.m.)
 Rating can be updated and the card background color will be change to darker shade.  Because the json doesn't have any rating, you can use the `age` in the result as the rating. Selecting a rating will increment the age (by the number of stars given) and change the card background color to darker shade. */

  export default {
    name: 'ReviewCard',

    data() {
      return {
        overallRaiting: 5,
        individualRaiting: 3,
      }
    },
  }
</script>

<style lang="scss" scoped>
.review-card{
  // Fonts
  font-family: Montserrat;
  display: flex;
  flex-direction: column;
  align-content: center;
  border-radius: 25px;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.513);
  max-width: 20em;

  .card-header{
    display: flex; 
    align-items: center;
    text-align: left;
    border-bottom: #D4DDDD .3px solid;
    padding: 7% 10%;
    
    h4{
      font-weight: 700;
    }
    p{
      color: #40918C;
      font-weight: 400;
    }

    .raiting{
      display: flex;
      align-items:center;
      justify-content: space-around;
    }

    .plus{
      padding: 1.5em;
      background-image: url(/plus.png), linear-gradient(
        184deg, rgba(243,246,246,1) 0%, rgba(243,246,246,1) 100%
      );
      border-radius: 12px;
      background-size: 100%; 
      background-position: center center;
      background-repeat: no-repeat;
    }
  }

  .card-body{
      padding-top: 10%;
    .card-information{
      display: flex;
      align-items: center;
      align-content: center;

      .avatar{
        height: 5em;
        width: auto;
        border-radius: 15px;
      }

    }

    .card-review{
      text-align: left;
      padding: 10%;
      font-weight: 400;
    }
  }

  .review-info{

  }

  .star-section{
    display: flex;
    justify-content: space-around;
    align-items: center;

    .star{
      padding: .5em;
      color: red;
      background-image: url(/star.png);
      background-size: contain;
    }
    
    color:#40918c;
  }
}
</style>