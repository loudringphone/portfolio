<template>

  <div id='backToTop'><b-button variant="outline-primary" title="back to the top" @mouseover="mouseOver()" @mouseout="mouseOut()" @click="backToTop()"><i class="bi bi-file-arrow-up" ></i></b-button><p>Back to the top and contact Winston now!</p></div>

</template>

<script>
export default {
    name:  'backtotop',
    data: function() {
            return {}
    },
    methods: {
    mouseOver(){
      const backToTop = document.querySelector('#backToTop')
      const p = backToTop.querySelector('p');
      p.style.color = 'salmon'
    },
    mouseOut(){
      const backToTop = document.querySelector('#backToTop')
      const p = backToTop.querySelector('p');
      p.style.color = 'currentcolor'
    },
    backToTop(){
      
      let target
      if (window.innerWidth <= 1000) {
        target = document.querySelector("#winston")
      } else {
        target = document.querySelector("#about")
      }
      target.scrollIntoView({ behavior: 'smooth', block: 'start' });
      document.body.style.pointerEvents = "none";
      function preventDefault(e) {
e.preventDefault();
}
      window.addEventListener("wheel", preventDefault, { passive:false })
      let scrolling = setInterval(() => {
        if (Math.floor(target.getBoundingClientRect().top) <= 10 && Math.floor(target.getBoundingClientRect().top) >= -10) {
          

          window.removeEventListener("wheel", preventDefault, { passive:false });
          document.body.style.pointerEvents = "auto";
          clearInterval(scrolling);
}
      }, 200);
      setTimeout(() => {
        if (document.body.style.pointerEvents === "none") {
          window.removeEventListener("wheel", preventDefault, { passive:false });
          document.body.style.pointerEvents = "auto";
          clearInterval(scrolling);
        }
      }, 1200);
    }
  }

    
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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

p {
  font-weight: bold;
}
</style>
