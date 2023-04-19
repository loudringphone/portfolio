<template>
  <div id="sancbook" @mouseover="mouseOver()" @touchstart="touchStart()">
    <button class="close-btn" @click="decreaseImageSize($event)" >&times;</button>
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
                    <img :src='feature.image'  :alt="feature.alt" style="max-width: 500px;" @click="increaseImageSize($event)">
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
                url: 'https://sancbook.herokuapp.com/',
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
    increaseImageSize(event) {
      if (window.innerWidth > 1000) {
        const img = event.target;
        const figcaption = img.parentElement.querySelector('figcaption');
        const sancbookDiv = document.querySelector('#sancbook')
        const sancbook = img.parentElement.parentElement;
        let sancbooks = sancbook.parentElement.querySelectorAll('.sancbook');
        sancbook.style.pointerEvents = 'auto';
        sancbook.style.filter = 'brightness(100%)';
        if (img.style.maxWidth === '500px') {
          const gridContainer = sancbookDiv.querySelector('.grid-container');
          const html = gridContainer.parentElement.parentElement.parentElement.parentElement
          html.style.pointerEvents = "none";
          html.style.overflow="hidden";
          gridContainer.scrollIntoView({ behavior: 'smooth', block: 'start' });
          setTimeout(() => {
            html.style.overflow="overlay";
            html.style.pointerEvents = "auto";
          }, 150);
          const btnClose = sancbookDiv.querySelector('.close-btn');
          btnClose.style.display = 'block';
          let phExisted = false;
          for (let sancbook of sancbooks) {
            if (sancbook.classList.contains('placeholder')) {
              phExisted = true;
            }
          }
          if (!phExisted) {
            const placeholder = sancbook.cloneNode(true);
            placeholder.classList.add('placeholder');
            placeholder.style.pointerEvents = 'none';
            placeholder.style.filter = 'brightness(30%)';
            sancbook.insertAdjacentElement('afterend', placeholder);
          }
          img.style.maxWidth = '900px';
          // closeButton.style.display = 'block';
          figcaption.style.fontSize = 'x-large';
          sancbook.classList.add('enlarged');
          sancbookDiv.style.background = 'black'


          const nav = document.querySelector('nav')
          const aboutDiv = document.querySelector('#about')
          const videostoreDiv = document.querySelector('#videostore')
          const utttDiv = document.querySelector('#uttt')
          const threelancersDiv = document.querySelector('#threelancers')
          const tutonetDiv = document.querySelector('#tutonet')
          const backToTop = document.querySelector('#backToTop')
          nav.style.pointerEvents = 'none' 
          aboutDiv.style.display = 'none' 
          videostoreDiv.style.display = 'none' 
          utttDiv.style.display = 'none' 
          threelancersDiv.style.display = 'none' 
          tutonetDiv.style.display = 'none' 
          backToTop.style.display = 'none'




          const a = sancbookDiv.querySelector('a');
          a.style.color = 'currentcolor';
          a.style.pointerEvents = 'none';
          sancbooks.forEach(sancbook => {
              sancbook.style.pointerEvents = 'none';
              sancbook.style.filter = 'brightness(30%)';
              sancbook.style.cursor = 'initial';
              sancbook.firstChild.style.opacity = '0.2'
          });
          sancbook.style.filter = 'brightness(100%)';
          sancbook.firstChild.style.opacity = '1'
          sancbook.style.pointerEvents = 'auto';

          const p = document.createElement('p');
          p.textContent = 'Press Esc to close'
          p.classList.add('esc')
          sancbookDiv.appendChild(p);
          window.addEventListener("keydown", function(event) {
            if (event.key === "Escape") {
              a.style.color = 'black'
              a.style.pointerEvents = 'auto'
              p.remove()
              sancbookDiv.style.background = '#FEF0E8';
              btnClose.style.display = 'none';
              figcaption.style.fontSize = 'initial';
              sancbook.classList.remove('enlarged');
              img.style.maxWidth = '500px'
              sancbooks = sancbook.parentElement.querySelectorAll('.sancbook');
              for (let sancbook of sancbooks) {
                sancbook.style.pointerEvents = 'auto';
                sancbook.style.filter = 'brightness(100%)';
                sancbook.style.cursor = 'pointer';
                sancbook.firstChild.style.opacity = '1'
                if (sancbook.classList.contains('placeholder')) {
                  sancbook.remove()
                }
              }

              const nav = document.querySelector('nav')
              const aboutDiv = document.querySelector('#about')
              const videostoreDiv = document.querySelector('#videostore')
              const utttDiv = document.querySelector('#uttt')
              const threelancersDiv = document.querySelector('#threelancers')
              const tutonetDiv = document.querySelector('#tutonet')
              const backToTop = document.querySelector('#backToTop')
              nav.style.pointerEvents = 'auto' 
              aboutDiv.style.display = 'block' 
              videostoreDiv.style.display = 'block' 
              utttDiv.style.display = 'block' 
              threelancersDiv.style.display = 'block' 
              tutonetDiv.style.display = 'block' 
              backToTop.style.display = 'block'

              sancbookDiv.scrollIntoView();
            }
          });
        }
      }
    },
    decreaseImageSize(event) {
      const sancbookDiv = document.querySelector("#sancbook")
      const enlarged = sancbookDiv.querySelector(".enlarged")
      enlarged.classList.remove('enlarged');
      const img = enlarged.querySelector('img')
      img.style.maxWidth = '500px';
      const figcaption = enlarged.querySelector('figcaption');
      const closeButton = event.target;
      
      const sancbook = closeButton.parentElement.parentElement;
      let sancbooks = sancbook.parentElement.querySelectorAll('.sancbook');
      for (let sancbook of sancbooks) {
        sancbook.style.pointerEvents = 'auto';
        sancbook.style.filter = 'brightness(100%)';
        sancbook.firstChild.style.opacity = '1';
        sancbook.style.cursor = 'pointer';
        if (sancbook.classList.contains('placeholder')) {
          sancbook.remove()
        }
      }
      const esc = sancbookDiv.querySelector('.esc')
      if (esc != null) {
        esc.remove()
      }
      sancbookDiv.style.background = '#FEF0E8';
      closeButton.style.display = 'none';
      figcaption.style.fontSize = 'initial';
      sancbook.classList.remove('enlarged');

      const a = sancbookDiv.querySelector('a')
      a.style.color = 'black'
      a.style.pointerEvents = 'auto'

      const nav = document.querySelector('nav')
      const aboutDiv = document.querySelector('#about')
      const videostoreDiv = document.querySelector('#videostore')
      const utttDiv = document.querySelector('#uttt')
      const threelancersDiv = document.querySelector('#threelancers')
      const tutonetDiv = document.querySelector('#tutonet')
      const backToTop = document.querySelector('#backToTop')
      nav.style.pointerEvents = 'auto' 
      aboutDiv.style.display = 'block' 
      videostoreDiv.style.display = 'block' 
      utttDiv.style.display = 'block' 
      threelancersDiv.style.display = 'block' 
      tutonetDiv.style.display = 'block' 
      backToTop.style.display = 'block'

      sancbookDiv.scrollIntoView();

    }
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
