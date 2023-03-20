<template>
  <div id="uttt" @mouseover="mouseOver()" @touchstart="touchStart()">
    <button class="close-btn" @click="decreaseImageSize($event)" >&times;</button>
    <h2>{{ title }}</h2>
    <p>{{ category }}</p>
    <a :href='url' target="_blank">{{ url }}</a>
    <p>{{ tech }}</p>
    <ul>
      <li v-for="d in description" :key="d.id">{{ d }}</li>
    </ul>

    <div class="grid-container" >
        <div v-for="feature in features" :key="feature.id" class="uttt">
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
  name:  'uttt',
  data: function() {
            return {
                title: 'Ultimate Tic-tac-toe',
                features: [
                  {image:require('@/assets/uttt/char-select.gif'), alt:'Character selection'},
                  {image:require('@/assets/uttt/play-with-ai.gif'), alt:'Play with AI'},
                  {image:require('@/assets/uttt/minimax.gif'), alt:'Minimax'},
                  {image:require('@/assets/uttt/options.gif'), alt:'Options'}
                ],
                url: 'https://loudringphone.github.io/ultimate-tictactoe/',
                category: 'Browser game',
                tech: 'Javascript | CSS | HTML | DOM',
                description: ['Interactive game and AI Algorithm (self-build AI and Minimax)', 'DOM manipulation with vanilla JavaScript', 'Character selection, Local storage, Board rest and Sound effect']
            };
        },
  methods: {
    mouseOver() {
      const utttDiv = document.querySelector('#uttt')
      
      const nav = document.querySelector('nav')
      
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'Ultimate Tic-tac-toe') {
          button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
          button.firstChild.classList.add("selected")
        }
      }
    },
    touchStart() {
      const utttDiv = document.querySelector('#uttt')
      
      const nav = document.querySelector('nav')
      
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'Ultimate Tic-tac-toe') {
          button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
          button.firstChild.classList.add("selected")
        }
      }
    },
    increaseImageSize(event) {
      if (window.innerWidth > 1000) {
        const img = event.target;
        const figcaption = img.parentElement.querySelector('figcaption');
        const utttDiv = document.querySelector('#uttt')
        const uttt = img.parentElement.parentElement;
        let uttts = uttt.parentElement.querySelectorAll('.uttt');
        uttt.style.pointerEvents = 'auto';
        uttt.style.filter = 'brightness(100%)';
        if (img.style.maxWidth === '500px') {
          const gridContainer = utttDiv.querySelector('.grid-container');
          const html = gridContainer.parentElement.parentElement.parentElement.parentElement
          html.style.pointerEvents = "none";
          html.style.overflow="hidden";
          gridContainer.scrollIntoView({ behavior: 'smooth', block: 'start' });
          setTimeout(() => {
            html.style.overflow="overlay";
            html.style.pointerEvents = "auto";
          }, 150);

          const btnClose = utttDiv.querySelector('.close-btn')
          btnClose.style.display = 'block'
          let phExisted = false;
          for (let uttt of uttts) {
            if (uttt.classList.contains('placeholder')) {
              phExisted = true;
            }
          }
          if (!phExisted) {
            const placeholder = uttt.cloneNode(true);
            placeholder.classList.add('placeholder');
            placeholder.style.pointerEvents = 'none';
            placeholder.style.filter = 'brightness(30%)';
            uttt.insertAdjacentElement('afterend', placeholder);
          }
          img.style.maxWidth = '900px';
          img.parentElement.parentElement.style.maxWidth = '900px';
          // closeButton.style.display = 'block';
          figcaption.style.fontSize = 'x-large';
          uttt.classList.add('enlarged');
          utttDiv.style.background = 'black'
          const a = utttDiv.querySelector('a');
          a.style.color = 'currentcolor';
          a.style.pointerEvents = 'none';
          uttts.forEach(uttt => {
              uttt.style.pointerEvents = 'none';
              uttt.style.filter = 'brightness(30%)';
              uttt.firstChild.style.opacity = '0.2'
              uttt.style.cursor = 'initial';
          });
          uttt.style.filter = 'brightness(100%)';
          uttt.firstChild.style.opacity = '1'
          uttt.style.pointerEvents = 'auto';

          const p = document.createElement('p');
          p.textContent = 'Press Esc to close'
          p.classList.add('esc')
          utttDiv.appendChild(p);
          window.addEventListener("keydown", function(event) {
          if (event.key === "Escape") {
            a.style.color = 'black'
            a.style.pointerEvents = 'auto'
            p.remove()
            utttDiv.style.background = '#DCDCF5';
            btnClose.style.display = 'none';
            figcaption.style.fontSize = 'initial';
            uttt.classList.remove('enlarged');
            img.style.maxWidth = '500px'
            uttts = uttt.parentElement.querySelectorAll('.uttt');
            for (let uttt of uttts) {
              uttt.style.pointerEvents = 'auto';
              uttt.style.filter = 'brightness(100%)';
              uttt.style.cursor = 'pointer';
              uttt.firstChild.style.opacity = '1'
              if (uttt.classList.contains('placeholder')) {
                uttt.remove()
              }
            }
          }
        });








        }
      }
    },
    decreaseImageSize(event) {
      const utttDiv = document.querySelector("#uttt")
      const enlarged = utttDiv.querySelector(".enlarged")
      enlarged.classList.remove('enlarged');
      const img = enlarged.querySelector('img')
      img.style.maxWidth = '500px';
      const figcaption = enlarged.querySelector('figcaption');
      const btnClose = event.target;
      
      const uttt = btnClose.parentElement.parentElement;
      let uttts = uttt.parentElement.querySelectorAll('.uttt');
      for (let uttt of uttts) {
        uttt.style.pointerEvents = 'auto';
        uttt.style.filter = 'brightness(100%)';
        uttt.style.cursor = 'pointer';
        uttt.firstChild.style.opacity = '1'
        if (uttt.classList.contains('placeholder')) {
          uttt.remove()
        }
      }
      const esc = utttDiv.querySelector('.esc')
      if (esc != null) {
        esc.remove()
      }
      utttDiv.style.background = '#DCDCF5';
      btnClose.style.display = 'none';
      figcaption.style.fontSize = 'initial';
      uttt.classList.remove('enlarged');

      const a = utttDiv.querySelector('a')
      a.style.color = 'black'
      a.style.pointerEvents = 'auto'
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
