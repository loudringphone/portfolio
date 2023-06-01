<template>
  <div id="threelancers" @mouseover="mouseOver()" @touchstart="touchStart()">
    <button class="close-btn" @click="decreaseImageSize($event)" >&times;</button>
        <h2>{{ title }}</h2>
        <p>{{ category }}</p>
        <a :href='url' target="_blank">{{ url }}</a>
        <p>{{ tech }}</p>
        <ul>
          <li v-for="d in description" :key="d.id">{{ d }}</li>
        </ul>
        <div class="grid-container" >
            <div v-for="feature in features" :key="feature.id" class="threelancers">
                <div class="image-container">
                    <img :src='feature.image'  :alt="feature.alt" @click="increaseImageSize($event)">
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
                  {image:require('@/assets/threelancers/react-interact-with-database.gif'), alt:'Using React as frontend to interact with Postgres in Ruby on Rails'},
                  {image:require('@/assets/threelancers/signup-authentication.gif'), alt:'Signup and error messages with Rails Active Record Validations'},
                  {image:require('@/assets/threelancers/jwt-sessions.gif'), alt:'JWT-based authentication implemented in Ruby on Rails'}
                ],
                url: '',
                category: 'Mobile marketplace',
                tech: 'React  | Ruby on Rails | postgreSQL | Netlify | Heroku',
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
    increaseImageSize(event) {
      if (window.innerWidth > 1000) {
        const img = event.target;
        const figcaption = img.parentElement.querySelector('figcaption');
        const threelancersDiv = document.querySelector('#threelancers')
        const threelancers = img.parentElement.parentElement;
        let threelancerss = threelancers.parentElement.querySelectorAll('.threelancers');
        threelancers.style.pointerEvents = 'auto';
        threelancers.style.filter = 'brightness(100%)';
        if (!threelancersDiv.querySelector('enlarged')) {
          const gridContainer = threelancersDiv.querySelector('.grid-container');
          const html = gridContainer.parentElement.parentElement.parentElement.parentElement
          html.style.pointerEvents = "none";
          html.style.overflow="hidden";
          console.log('scrolling')
          // gridContainer.parentElement.parentElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
          setTimeout(() => {
            html.style.overflow="overlay";
            html.style.pointerEvents = "auto";
          }, 150);

          const btnClose = threelancersDiv.querySelector('.close-btn')
          btnClose.style.display = 'block'
          let phExisted = false;
          for (let threelancers of threelancerss) {
            if (threelancers.classList.contains('placeholder')) {
              phExisted = true;
            }
          }
          if (!phExisted) {
            const placeholder = threelancers.cloneNode(true);
            placeholder.classList.add('placeholder');
            placeholder.style.pointerEvents = 'none';
            placeholder.style.filter = 'brightness(30%)';
            threelancers.insertAdjacentElement('afterend', placeholder);
          }


          const grandpa = img.parentElement.parentElement
         
        if (!img.getAttribute('src').includes('jwt-sessions')) {
            grandpa.style.width = '450px';
            grandpa.style.height = '750px'
            img.style.width = '450px';
        }
        else {
            grandpa.style.width = '900px';
            grandpa.style.height = '665px'
            img.style.width = '900px';
        }
                
         
            
         
          // closeButton.style.display = 'block';
          figcaption.style.fontSize = 'x-large';
          threelancers.classList.add('enlarged');
          threelancersDiv.style.background = 'black'

          const nav = document.querySelector('nav')
          const aboutDiv = document.querySelector('#about')
          const videostoreDiv = document.querySelector('#videostore')
          const sancbookDiv = document.querySelector('#sancbook')
          const utttDiv = document.querySelector('#uttt')
          const tutonetDiv = document.querySelector('#tutonet')
          const backToTop = document.querySelector('#backToTop')
          // nav.style.pointerEvents = 'none' 
          // aboutDiv.style.display = 'none' 
          // videostoreDiv.style.display = 'none' 
          // sancbookDiv.style.display = 'none' 
          // utttDiv.style.display = 'none' 
          // tutonetDiv.style.display = 'none' 
          // backToTop.style.display = 'none'


          const a = threelancersDiv.querySelector('a');
          a.style.color = 'currentcolor';
          a.style.pointerEvents = 'none';
          threelancerss.forEach(threelancers => {
              threelancers.style.pointerEvents = 'none';
              threelancers.style.filter = 'brightness(30%)';
              threelancers.style.cursor = 'initial';
              threelancers.firstChild.style.opacity = '0.2'
          });
          threelancers.style.filter = 'brightness(100%)';
          threelancers.firstChild.style.opacity = '1'
          threelancers.style.pointerEvents = 'auto';

          
          const p = document.createElement('p');
          p.textContent = 'Press Esc to close'
          p.classList.add('esc')
          threelancersDiv.appendChild(p);
          window.addEventListener("keydown", function(event) {
            if (event.key === "Escape") {
              a.style.color = 'black'
              a.style.pointerEvents = 'auto'
              p.remove()
              threelancersDiv.style.background = '#DCF5DC';
              btnClose.style.display = 'none';
              figcaption.style.fontSize = 'initial';
              threelancers.classList.remove('enlarged');
              if (!img.getAttribute('src').includes('jwt-sessions')) {
            grandpa.style.width = '300px';
            grandpa.style.height = 'auto'
            img.style.width = '300px';
            }
            else {  
                grandpa.style.width = '500px';
                grandpa.style.height = 'auto'
                img.style.width = '500px';
            }
              threelancerss = threelancers.parentElement.querySelectorAll('.threelancers');
              for (let threelancers of threelancerss) {
                threelancers.style.pointerEvents = 'auto';
                threelancers.style.filter = 'brightness(100%)';
                threelancers.style.cursor = 'pointer';
                threelancers.firstChild.style.opacity = '1'
                if (threelancers.classList.contains('placeholder')) {
                  threelancers.remove()
                }
              }

              const nav = document.querySelector('nav')
              const aboutDiv = document.querySelector('#about')
              const videostoreDiv = document.querySelector('#videostore')
              const sancbookDiv = document.querySelector('#sancbook')
              const utttDiv = document.querySelector('#uttt')
              const tutonetDiv = document.querySelector('#tutonet')
              const backToTop = document.querySelector('#backToTop')
              nav.style.pointerEvents = 'auto' 
              aboutDiv.style.display = 'block' 
              videostoreDiv.style.display = 'block' 
              sancbookDiv.style.display = 'block' 
              utttDiv.style.display = 'block' 
              tutonetDiv.style.display = 'block' 
              backToTop.style.display = 'block'

              // threelancersDiv.scrollIntoView()
            }
          });
        }
      }
    },
    decreaseImageSize(event) {
      const threelancersDiv = document.querySelector("#threelancers")
      const enlarged = threelancersDiv.querySelector(".enlarged")
      enlarged.classList.remove('enlarged');
      const img = enlarged.querySelector('img')
      const figcaption = enlarged.querySelector('figcaption');
      const closeButton = event.target;
      
      const threelancers = closeButton.parentElement.parentElement;
      let threelancerss = threelancers.parentElement.querySelectorAll('.threelancers');
      for (let threelancers of threelancerss) {
        threelancers.style.pointerEvents = 'auto';
        threelancers.style.filter = 'brightness(100%)';
        threelancers.firstChild.style.opacity = '1';
        threelancers.style.cursor = 'pointer';
        if (threelancers.classList.contains('placeholder')) {
          threelancers.remove()
        }
      }
      const esc = threelancersDiv.querySelector('.esc')
      if (esc != null) {
        esc.remove()
      }
      threelancersDiv.style.background = '#DCF5DC';
      closeButton.style.display = 'none';
      figcaption.style.fontSize = 'initial';
      threelancers.classList.remove('enlarged');

      const grandpa = img.parentElement.parentElement
        if (!img.getAttribute('src').includes('jwt-sessions')) {
        grandpa.style.width = '300px';
        grandpa.style.height = 'auto'
        img.style.width = '300px';
        }
        else {
            grandpa.style.width = '500px';
            grandpa.style.height = 'auto'
            img.style.width = '500px';
        }

        const a = threelancersDiv.querySelector('a')
        a.style.color = 'black'
        a.style.pointerEvents = 'auto'

        const nav = document.querySelector('nav')
        const aboutDiv = document.querySelector('#about')
        const videostoreDiv = document.querySelector('#videostore')
        const sancbookDiv = document.querySelector('#sancbook')
        const utttDiv = document.querySelector('#uttt')
        const tutonetDiv = document.querySelector('#tutonet')
        const backToTop = document.querySelector('#backToTop')
        nav.style.pointerEvents = 'auto' 
        aboutDiv.style.display = 'block' 
        videostoreDiv.style.display = 'block' 
        sancbookDiv.style.display = 'block' 
        utttDiv.style.display = 'block' 
        tutonetDiv.style.display = 'block' 
        backToTop.style.display = 'block'

        // threelancersDiv.scrollIntoView()

    }
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
