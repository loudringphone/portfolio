<template>
  <div id="uttt" @mouseover="mouseOver()" @touchstart="touchStart()">
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
        <div v-for="feature in features" :key="feature.id" class="uttt">
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
                git: 'https://github.com/loudringphone/ultimate-tictactoe',
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
