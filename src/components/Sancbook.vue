<template>
  <div id="sancbook" @mouseover="mouseOver()" @touchstart="touchStart()">
        <h2>{{ title }}</h2>
        <p>{{ category }}</p>
        <a :href='url' target="_blank">{{ url }}</a>
        <p>{{ tech }}</p>
        <ul>
          <li v-for="d in description" :key="d.id">{{ d }}</li>
        </ul>
        <div class="grid-container" >
            <div v-for="feature in features" :key="feature.id" class="sancbook">
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
  name:  'sancbook',
  data: function() {
            return {
                title: 'Sancbook',
                features: [
                  {image:require('@/assets/sancbook/sending-data-from-rails-to-js.gif'), alt:'Sending data from rails controllers to js to produce the interactive world map with Gon'},
                  {image:require('@/assets/sancbook/web-scraping.gif'), alt:'Scraping data from Wikipedia and Youtube with Nokogiri and YouTube Data API'},
                  {image:require('@/assets/sancbook/instant-messaging.gif'), alt:'Instant messaging with Ajax'},
                  {image:require('@/assets/sancbook/signup.gif'), alt:'Signup and error messages with Rails Active Record Validations'}
                ],
                url: 'https://youtu.be/7fH1DrjlxoU/',
                category: 'Social media platform',
                tech: 'Ruby on Rails | postgreSQL | SCSS | Heroku',
                description: ['CRUD systems using Ruby on Rails and PostgreSQL', 'Gon, Nokogiri, Cloudinary, Google search API & etc', 'Instant messaging with Ajax']
            };
        },
  methods: {
    mouseOver() {
      const nav = document.querySelector('nav')
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'Sancbook') {
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
        if (button.firstChild.textContent === 'Sancbook') {
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
