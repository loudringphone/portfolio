<template>
  <div id="videostore" @mouseover="mouseOver()" @touchstart="touchStart()">
    <button class="close-btn" @click="decreaseImageSize($event)" >&times;</button>
        <h2>{{ title }}</h2>
        <p>{{ category }}</p>
        <a :href='url' target="_blank">{{ url }}</a>
        <p>{{ tech }}</p>
        <ul>
          <li v-for="d in description" :key="d.id">{{ d }}</li>
        </ul>
        <!-- <div class="grid-container" >
            <div v-for="feature in features" :key="feature.id" class="videostore">
                <div class="image-container">
                    <img :src='feature.image'  :alt="feature.alt" style="max-width: 500px;" @click="increaseImageSize($event)">
                    <figcaption>{{feature.alt}}</figcaption>
                </div>
            </div>
        </div> -->
    </div>

</template>

<script>
export default {
  name:  'videostore',
  data: function() {
            return {
                title: 'Video Store',
                features: [
                  {image:require('@/assets/sancbook/sending-data-from-rails-to-js.gif'), alt:'Sending data from rails controllers to js to produce the interactive world map with Gon'},
                  {image:require('@/assets/sancbook/web-scraping.gif'), alt:'Scraping data from Wikipedia and Youtube with Nokogiri and YouTube Data API'},
                  {image:require('@/assets/sancbook/instant-messaging.gif'), alt:'Instant messaging with Ajax'},
                  {image:require('@/assets/sancbook/signup.gif'), alt:'Signup and error messages with Rails Active Record Validations'}
                ],
                url: 'https://videostore.netlify.app/',
                category: 'eCommerce platform',
                tech: 'React | Firebase | Rowy | Netlify',
                description: ['Work in Progress']
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
    increaseImageSize(event) {
      if (window.innerWidth > 1000) {
        const img = event.target;
        const figcaption = img.parentElement.querySelector('figcaption');
        const videostoreDiv = document.querySelector('#videostore')
        const videostore = img.parentElement.parentElement;
        let videostores = videostore.parentElement.querySelectorAll('.videostore');
        videostore.style.pointerEvents = 'auto';
        videostore.style.filter = 'brightness(100%)';
        const btnClose = videostoreDiv.querySelector('.close-btn');
        btnClose.style.display = 'block';
        if (img.style.maxWidth === '500px') {
          const gridContainer = videostoreDiv.querySelector('.grid-container');
          const html = gridContainer.parentElement.parentElement.parentElement.parentElement
          html.style.pointerEvents = "none";
          html.style.overflow="hidden";
          gridContainer.scrollIntoView({ behavior: 'smooth', block: 'start' });
          setTimeout(() => {
            html.style.overflow="overlay";
            html.style.pointerEvents = "auto";
          }, 150);
          
          let phExisted = false;
          for (let videostore of videostores) {
            if (videostore.classList.contains('placeholder')) {
              phExisted = true;
            }
          }
          if (!phExisted) {
            const placeholder = videostore.cloneNode(true);
            placeholder.classList.add('placeholder');
            placeholder.style.pointerEvents = 'none';
            placeholder.style.filter = 'brightness(30%)';
            videostore.insertAdjacentElement('afterend', placeholder);
          }
          img.style.maxWidth = '900px';
          // closeButton.style.display = 'block';
          figcaption.style.fontSize = 'x-large';
          videostore.classList.add('enlarged');

          videostoreDiv.style.background = 'black'

            const nav = document.querySelector('nav')
            const aboutDiv = document.querySelector('#about')
            const utttDiv = document.querySelector('#uttt')
            const sancbookDiv = document.querySelector('#sancbook')
            const threelancersDiv = document.querySelector('#threelancers')
            const tutonetDiv = document.querySelector('#tutonet')
            const backToTop = document.querySelector('#backToTop')
            nav.style.pointerEvents = 'none' 
            aboutDiv.style.display = 'none' 
            utttDiv.style.display = 'none' 
            sancbookDiv.style.display = 'none' 
            threelancersDiv.style.display = 'none' 
            tutonetDiv.style.display = 'none' 
            backToTop.style.display = 'none' 


          const a = videostoreDiv.querySelector('a');
          a.style.color = 'currentcolor';
          a.style.pointerEvents = 'none';

            
        
          videostores.forEach(videostore => {
              videostore.style.pointerEvents = 'none';
              videostore.style.filter = 'brightness(30%)';
              videostore.style.cursor = 'initial';
              videostore.firstChild.style.opacity = '0.2'
          });
          videostore.style.filter = 'brightness(100%)';
          videostore.firstChild.style.opacity = '1'
          videostore.style.pointerEvents = 'auto';

          const p = document.createElement('p');
          p.textContent = 'Press Esc to close'
          p.classList.add('esc')
          videostoreDiv.appendChild(p);
          window.addEventListener("keydown", function(event) {
            if (event.key === "Escape") {
              a.style.color = 'black'
              a.style.pointerEvents = 'auto'
              p.remove()
              videostoreDiv.style.background = '#f3ffd9';
              btnClose.style.display = 'none';
              figcaption.style.fontSize = 'initial';
              videostore.classList.remove('enlarged');
              img.style.maxWidth = '500px'
              videostores = videostore.parentElement.querySelectorAll('.videostore');
              for (let videostore of videostores) {
                videostore.style.pointerEvents = 'auto';
                videostore.style.filter = 'brightness(100%)';
                videostore.style.cursor = 'pointer';
                videostore.firstChild.style.opacity = '1'
                if (videostore.classList.contains('placeholder')) {
                  videostore.remove()
                }
              }

                const nav = document.querySelector('nav')
                const aboutDiv = document.querySelector('#about')
                const utttDiv = document.querySelector('#uttt')
                const sancbookDiv = document.querySelector('#sancbook')
                const threelancersDiv = document.querySelector('#threelancers')
                const tutonetDiv = document.querySelector('#tutonet')
                const backToTop = document.querySelector('#backToTop')
                nav.style.pointerEvents = 'auto' 
                aboutDiv.style.display = 'block' 
                utttDiv.style.display = 'block' 
                sancbookDiv.style.display = 'block' 
                threelancersDiv.style.display = 'block' 
                tutonetDiv.style.display = 'block' 
                backToTop.style.display = 'block' 

                videostoreDiv.scrollIntoView()

            }
          });
        }
      }
    },
    decreaseImageSize(event) {
      const videostoreDiv = document.querySelector("#videostore")
      const enlarged = videostoreDiv.querySelector(".enlarged")
      enlarged.classList.remove('enlarged');
      const img = enlarged.querySelector('img')
      img.style.maxWidth = '500px';
      const figcaption = enlarged.querySelector('figcaption');
      const closeButton = event.target;
      
      const videostore = closeButton.parentElement.parentElement;
      let videostores = videostore.parentElement.querySelectorAll('.videostore');
      for (let videostore of videostores) {
        videostore.style.pointerEvents = 'auto';
        videostore.style.filter = 'brightness(100%)';
        videostore.firstChild.style.opacity = '1';
        videostore.style.cursor = 'pointer';
        if (videostore.classList.contains('placeholder')) {
          videostore.remove()
        }
      }
      const esc = videostoreDiv.querySelector('.esc')
      if (esc != null) {
        esc.remove()
      }
      videostoreDiv.style.background = '#f3ffd9';
      closeButton.style.display = 'none';
      figcaption.style.fontSize = 'initial';
      videostore.classList.remove('enlarged');

      const a = videostoreDiv.querySelector('a')
      a.style.color = 'black'
      a.style.pointerEvents = 'auto'

        const nav = document.querySelector('nav')
        const aboutDiv = document.querySelector('#about')
        const utttDiv = document.querySelector('#uttt')
        const sancbookDiv = document.querySelector('#sancbook')
        const threelancersDiv = document.querySelector('#threelancers')
        const tutonetDiv = document.querySelector('#tutonet')
        const backToTop = document.querySelector('#backToTop')
        nav.style.pointerEvents = 'auto' 
        aboutDiv.style.display = 'block' 
        utttDiv.style.display = 'block' 
        sancbookDiv.style.display = 'block' 
        threelancersDiv.style.display = 'block' 
        tutonetDiv.style.display = 'block' 
        backToTop.style.display = 'block'

        videostoreDiv.scrollIntoView()


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
