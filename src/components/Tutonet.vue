<template>
  <div id="tutonet" @mouseover="mouseOver()" @touchstart="touchStart()">
    <button class="close-btn" @click="decreaseImageSize($event)" >&times;</button>
    <h2>{{ title }}</h2>
    <p>{{ category }}</p>
    <a :href='url' target="_blank">{{ url }}</a>
    <p>{{ tech }}</p>
    <ul>
        <li v-for="d in description" :key="d.id">{{ d }}</li>
    </ul>
    <div class="grid-container" >
        <div v-for="feature in features" :key="feature.id" class="tutonet">
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
  name:  'tutonet',
  data: function() {
            return {
                title: 'Tutonet',
                features: [
                  {image:require('@/assets/tutonet/create-record.gif'), alt:'Create new record with manipulated dropdown list'},
                  {image:require('@/assets/tutonet/table-manipulation.gif'), alt:'Data validation with existing records'},
                  {image:require('@/assets/tutonet/dropdown-list-manipulation.gif'), alt:'Manipulated dropdown list based on preselected values'},
                  {image:require('@/assets/tutonet/filter-table.gif'), alt:'Filterable table'}
                ],
                url: 'https://tutonet.netlify.app/',
                category: 'Task management',
                tech: 'Vue | Quasar | Supabase | Netlify',
                description: ['DOM manipulation with vue', 'Supabase database', 'Quasar framework']
            };
        },
  methods: {
    mouseOver() {
      const tutonetDiv = document.querySelector('#tutonet')
      
      const nav = document.querySelector('nav')
      
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'Tutonet') {
          button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
          button.firstChild.classList.add("selected")
        }
      }
    },
    touchStart() {
      const tutonetDiv = document.querySelector('#tutonet')
      
      const nav = document.querySelector('nav')
      
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'Tutonet') {
          button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
          button.firstChild.classList.add("selected")
        }
      }
    },
    increaseImageSize(event) {
      if (window.innerWidth > 1000) {
        const img = event.target;
        const figcaption = img.parentElement.querySelector('figcaption');
        const tutonetDiv = document.querySelector('#tutonet')
        const tutonet = img.parentElement.parentElement;
        let tutonets = tutonet.parentElement.querySelectorAll('.tutonet');
        tutonet.style.pointerEvents = 'auto';
        tutonet.style.filter = 'brightness(100%)';
        if (img.style.maxWidth === '500px') {
          const h2 = tutonetDiv.querySelector('h2');
          const html = h2.parentElement.parentElement.parentElement.parentElement
          html.style.pointerEvents = "none";
          html.style.overflow="hidden";
          h2.scrollIntoView({ behavior: 'smooth', block: 'start' });
          setTimeout(() => {
            html.style.overflow="overlay";
            html.style.pointerEvents = "auto";
          }, 150);

          const btnClose = tutonetDiv.querySelector('.close-btn')
          btnClose.style.display = 'block'
          let phExisted = false;
          for (let tutonet of tutonets) {
            if (tutonet.classList.contains('placeholder')) {
              phExisted = true;
            }
          }
          if (!phExisted) {
            const placeholder = tutonet.cloneNode(true);
            placeholder.classList.add('placeholder');
            placeholder.style.pointerEvents = 'none';
            placeholder.style.filter = 'brightness(30%)';
            tutonet.insertAdjacentElement('afterend', placeholder);
          }
          img.style.maxWidth = '900px';
          img.parentElement.parentElement.style.maxWidth = '900px';
          // closeButton.style.display = 'block';
          figcaption.style.fontSize = 'x-large';
          figcaption.style.height = '100%';
          figcaption.style.width = '165px';

          tutonet.classList.add('enlarged');
          tutonetDiv.style.background = 'black'

          const nav = document.querySelector('nav')
          const aboutDiv = document.querySelector('#about')
          const videostoreDiv = document.querySelector('#videostore')
          const sancbookDiv = document.querySelector('#sancbook')
          const utttDiv = document.querySelector('#uttt')
          const threelancersDiv = document.querySelector('#threelancers')
          const backToTop = document.querySelector('#backToTop')
          nav.style.pointerEvents = 'none' 
          aboutDiv.style.display = 'none' 
          videostoreDiv.style.display = 'none' 
          sancbookDiv.style.display = 'none' 
          utttDiv.style.display = 'none' 
          threelancersDiv.style.display = 'none' 
          backToTop.style.display = 'none'

          const a = tutonetDiv.querySelector('a');
          const ps = tutonetDiv.querySelectorAll('p');
          const ul = tutonetDiv.querySelector('ul');
          a.style.color = 'currentcolor';
          h2.style.color = 'currentcolor';
          ps.forEach(e => {
            e.style.color = 'currentcolor';
          })
          ul.style.color = 'currentcolor';
          a.style.pointerEvents = 'none';
          tutonets.forEach(tutonet => {
              tutonet.style.pointerEvents = 'none';
              tutonet.style.filter = 'brightness(30%)';
              tutonet.firstChild.style.opacity = '0.2'
              tutonet.style.cursor = 'initial';
          });
          tutonet.style.filter = 'brightness(100%)';
          tutonet.firstChild.style.opacity = '1'
          tutonet.style.pointerEvents = 'auto';

          const p = document.createElement('p');
          p.textContent = 'Press Esc to close'
          p.classList.add('esc')
          tutonetDiv.appendChild(p);
          window.addEventListener("keydown", function(event) {
          if (event.key === "Escape") {
            a.style.color = 'black';
            a.style.pointerEvents = 'auto';
            p.remove()
            tutonetDiv.style.background = '#ffd7de';
            btnClose.style.display = 'none';
            figcaption.style.fontSize = 'initial';
            figcaption.style.height = 'auto';
            figcaption.style.width = '100%';
            tutonet.classList.remove('enlarged');
            img.style.maxWidth = '500px'
            tutonets = tutonet.parentElement.querySelectorAll('.tutonet');
            for (let tutonet of tutonets) {
              tutonet.style.pointerEvents = 'auto';
              tutonet.style.filter = 'brightness(100%)';
              tutonet.style.cursor = 'pointer';
              tutonet.firstChild.style.opacity = '1'
              if (tutonet.classList.contains('placeholder')) {
                tutonet.remove()
              }
            }

            const nav = document.querySelector('nav')
            const aboutDiv = document.querySelector('#about')
            const videostoreDiv = document.querySelector('#videostore')
            const sancbookDiv = document.querySelector('#sancbook')
            const utttDiv = document.querySelector('#uttt')
            const threelancersDiv = document.querySelector('#threelancers')
            const backToTop = document.querySelector('#backToTop')
            nav.style.pointerEvents = 'auto' 
            aboutDiv.style.display = 'block' 
            videostoreDiv.style.display = 'block' 
            sancbookDiv.style.display = 'block' 
            utttDiv.style.display = 'block' 
            threelancersDiv.style.display = 'block' 
            backToTop.style.display = 'block'

            tutonetDiv.scrollIntoView()
          }
        });
        }
      }
    },
    decreaseImageSize(event) {
      const tutonetDiv = document.querySelector("#tutonet")
      const enlarged = tutonetDiv.querySelector(".enlarged")
      enlarged.classList.remove('enlarged');
      const img = enlarged.querySelector('img')
      img.style.maxWidth = '500px';
      const figcaption = enlarged.querySelector('figcaption');
      const btnClose = event.target;
      
      const tutonet = btnClose.parentElement.parentElement;
      let tutonets = tutonet.parentElement.querySelectorAll('.tutonet');
      for (let tutonet of tutonets) {
        tutonet.style.pointerEvents = 'auto';
        tutonet.style.filter = 'brightness(100%)';
        tutonet.style.cursor = 'pointer';
        tutonet.firstChild.style.opacity = '1'
        if (tutonet.classList.contains('placeholder')) {
          tutonet.remove()
        }
      }
      const esc = tutonetDiv.querySelector('.esc')
      if (esc != null) {
        esc.remove()
      }
      tutonetDiv.style.background = '#ffd7de';
      btnClose.style.display = 'none';
      figcaption.style.fontSize = 'initial';
      figcaption.style.height = 'auto';
      figcaption.style.width = '100%';
      tutonet.classList.remove('enlarged');

      const a = tutonetDiv.querySelector('a');
      a.style.color = 'black';
      a.style.pointerEvents = 'auto';


      const nav = document.querySelector('nav')
      const aboutDiv = document.querySelector('#about')
      const videostoreDiv = document.querySelector('#videostore')
      const sancbookDiv = document.querySelector('#sancbook')
      const utttDiv = document.querySelector('#uttt')
      const threelancersDiv = document.querySelector('#threelancers')
      const backToTop = document.querySelector('#backToTop')
      nav.style.pointerEvents = 'auto' 
      aboutDiv.style.display = 'block' 
      videostoreDiv.style.display = 'block' 
      sancbookDiv.style.display = 'block' 
      utttDiv.style.display = 'block' 
      threelancersDiv.style.display = 'block' 
      backToTop.style.display = 'block'

      tutonetDiv.scrollIntoView()


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
button.btn.btn-outline-primary {
    background-color: lightskyblue;
    color: white;
    border-color: navy;
    border-left-width: thick;
    border-bottom-width: thick;
    border-radius: 10px;
    margin: 30px 0 10px 0;
  }

  button.btn.btn-outline-primary:hover {
    background-color: lightyellow;
    color: salmon;
    border-color: salmon;
    
  }

  button.btn.btn-outline-primary:active {
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

  ::before {
    font-size: xxx-large;
  }
</style>
