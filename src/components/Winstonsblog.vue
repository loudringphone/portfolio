<template>
  <div id="winstonsblog" @mouseover="mouseOver()" @touchstart="touchStart()">
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
            <div v-for="feature in features" :key="feature.id" class="winstonsblog">
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
  name:  'winstonsblog',
  data: function() {
            return {
                title: "Winston's Blog",
                features: [
                  {image:require('@/assets/winstonblog/blog.gif'), alt:'Blog editor'},
                  {image:require('@/assets/winstonblog/warning-before-leaving.gif'), alt:'Warning before leaving the edit page'},
                  {image:require('@/assets/winstonblog/image-upload-and-label-selection.gif'), alt:'Image upload quota for each post'},
                  {image:require('@/assets/winstonblog/post-categories.gif'), alt:'Posts are fetched based on their categories or labels'}
                ],
                url: 'https://winstonsblog.netlify.app/',
                git: 'https://github.com/loudringphone/blog-editor',
                category: 'Blog editor',
                tech: 'ReactJS | Quill | Firebase | Rowy | Netlify',
                description: ["Blog editor which can be used as a headless CMS to maintain the blog posts on company webpages."]
            };
        },
  methods: {
    mouseOver() {
      const nav = document.querySelector('nav')
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === "Winston's Blog") {
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
        if (button.firstChild.textContent === "Winston's Blog") {
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
