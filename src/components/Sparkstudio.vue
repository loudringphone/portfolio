<template>
  <div id="sparkstudio" @mouseover="mouseOver()" @touchstart="touchStart()">
        <h2>{{ title }}</h2>
        <p>{{ category }}</p>
        <a :href='url' target="_blank">{{ url }}</a>
        <br>
        <a :href='git' target="_blank">{{ git }}</a>
        <p>{{ tech }}</p>
        <ul>
          <li v-for="d in description" :key="d.id">{{ d }}</li>
        </ul>
        <div class="grid-container" >
            <div v-for="feature in features" :key="feature.id" class="sparkstudio">
                <div class="image-container">
                    <img :src='feature.image'  :alt="feature.alt" style="max-width: 500px;">
                    <figcaption>{{feature.alt}}</figcaption>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
export default {
  name:  'sparkstudio',
  data: function() {
            return {
                title: 'Spark Studio',
                features: [
                  {image:require('@/assets/sparkstudio/sparkstudio.gif'), alt:'Home page'},
                  {image:require('@/assets/sparkstudio/portfolio.gif'), alt:'Portfolio page'},
                  {image:require('@/assets/sparkstudio/contact.gif'), alt:'Contact page'},
                  {image:require('@/assets/sparkstudio/gitstats.gif'), alt:'Git repository statistics of this Collab-athon over the weekend'}
                ],
                url: 'https://sparkstudio.netlify.app/',
                git: 'https://github.com/loudringphone/product-development-agency',
                category: 'Product development agency',
                tech: 'ReactJS | Firebase | Rowy | Netlify',
                description: ["For the General Assembly Australia's Collab-athon over the weekend from 30 Jun to 2 July 2023."]
            };
        },
  methods: {
    mouseOver() {
      const nav = document.querySelector('nav')
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'Spark Studio') {
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
        if (button.firstChild.textContent === 'Spark Studio') {
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
</style>
