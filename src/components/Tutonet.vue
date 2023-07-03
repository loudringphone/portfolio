<template>
  <div id="tutonet" @mouseover="mouseOver()" @touchstart="touchStart()">
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
        <div v-for="feature in features" :key="feature.id" class="tutonet">
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
                git: 'https://github.com/loudringphone/tutonet',
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
