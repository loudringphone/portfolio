<template>
  <div id="videostore" @mouseover="mouseOver()" @touchstart="touchStart()">
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
            <div v-for="feature in features" :key="feature.id" class="videostore">
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
  name:  'videostore',
  data: function() {
            return {
                title: 'Video Store',
                features: [
                  {image:require('@/assets/videostore/rowy-and-using-derivative-functions.gif'), alt:'Using rowy as the content management system to visualise database'},
                  {image:require('@/assets/videostore/wishlist-and-cart.gif'), alt:'Dynamic cart and wishlist using Redux and Firebase'},
                  {image:require('@/assets/videostore/addresses.gif'), alt:'Dynamic address input fields by manipulating state in React'},
                  {image:require('@/assets/videostore/stripe.gif'), alt:'Stripe client and server integration using Firebase Cloud functions and Stripe webhooks'}
                ],
                url: 'https://videostore.netlify.app/',
                git: 'https://github.com/loudringphone/videostore',
                category: 'eCommerce platform',
                tech: 'ReactJS | Redux | Firebase | Stripe | Rowy | Netlify',
                description: ['Stripe client and server integration with Firebase and ReactJS', 'Firebase Cloud Functions and webhooks']
            };
        },
  methods: {
    mouseOver() {
      const nav = document.querySelector('nav')
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'Video Store') {
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
        if (button.firstChild.textContent === 'Video Store') {
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
