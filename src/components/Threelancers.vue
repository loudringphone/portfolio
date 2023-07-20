<template>
  <div id="threelancers" @mouseover="mouseOver()" @touchstart="touchStart()">
            <h2>{{ title }}</h2>
        <p>{{ category }}</p>
        <a :href='url' target="_blank">{{ url }}</a>
        <a :href='git1' target="_blank">{{ git1 }}</a>
        <a :href='git2' target="_blank">{{ git2 }}</a>
        <p>{{ tech }}</p>
        <ul>
          <li v-for="d in description" :key="d.id">{{ d }}</li>
        </ul>
        <div class="grid-container" >
            <div v-for="feature in features" :key="feature.id" class="threelancers">
                <div class="image-container">
                    <img :src='feature.image'  :alt="feature.alt">
                    <figcaption>{{feature.alt}}</figcaption>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
export default {
  name:  'threeLancers',
  data: function() {
            return {
                title: '3Lancers',
                features: [
                  {image:require('@/assets/threelancers/google-maps-api.gif'), alt:'Google Maps API with fun animation'},
                  {image:require('@/assets/threelancers/react-interact-with-database.gif'), alt:'Using ReactJS as frontend to interact with Postgres in Ruby on Rails'},
                  {image:require('@/assets/threelancers/signup-authentication.gif'), alt:'Signup and error messages with Rails Active Record Validations'},
                  {image:require('@/assets/threelancers/jwt-sessions.gif'), alt:'JWT-based authentication implemented in Ruby on Rails'}
                ],
                url: '',
                git1: 'https://github.com/loudringphone/3lancers_server',
                git2: 'https://github.com/loudringphone/3lancers_client',
                category: 'Mobile marketplace',
                tech: 'ReactJS  | Ruby on Rails | postgreSQL | Netlify | Heroku',
                description: ['Ruby on Rails as back-end', 'React as front-end', 'JWT token sign-in', 'Google Maps Geocoding API']
            };
        },
  methods: {
    mouseOver() {
      const nav = document.querySelector('nav')
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === '3Lancers') {
          button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
          button.firstChild.classList.add("selected")
        }
      }
    },
    touchStart() {
      const nav = document.querySelector('nav')
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === '3Lancers') {
          button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
          button.firstChild.classList.add("selected")
        }
      }
    },
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.grid-container {
  display:relative;
    display: grid;
    grid-template-columns: repeat(3, 300px);
    grid-template-rows: repeat(2, 1fr);
    gap: 20px;
    max-height: 950px;
    overflow: hidden;
}
div.threelancers:nth-child(-n + 3) {
    width: 300px;
}
img {
  width: 300px;
}
div.threelancers:nth-child(4) {
    grid-column: 1/4;
    width: 500px;
}
div.threelancers:nth-child(4) > div > img {
    width: 500px;
}

.placeholder {
  width: 300px !important;
}
.esc {
    position: absolute;
    top: 450% !important;
}
a {
    color: black;
}
figcaption {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    padding: 5px 0 5px 10px;
    background-color: lightslategray;
    color: cornsilk;
    text-align: left;
}
@media (max-width: 1000px) {
  div#threelancers > div.grid-container{
    text-align: center;
    text-align: -webkit-center;
  }
  .grid-container {
    display:contents;
    max-height:max-content
  }
  div.threelances {
    padding-left: 0px;
    margin-left: 0px;
  }
  img {
  width: 250px;
  }
  div.threelancers:nth-child(4) {
      width: 90vw;
      max-width: 500px;
  }
  div.threelancers:nth-child(4) > div > img {
    width: 90vw;
    max-width: 500px;
}
}

</style>
