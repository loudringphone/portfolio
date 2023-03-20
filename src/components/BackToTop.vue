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
      const backToTop = document.querySelector('#backToTop')
      backToTop.firstChild.style.backgroundColor = 'lightskyblue';
      backToTop.firstChild.style.color = 'white';
      backToTop.firstChild.style.borderColor = 'navy';

      backToTop.firstChild.addEventListener('mouseover', function(){
        this.style.backgroundColor = 'lightyellow';
        this.style.color = 'salmon';
        this.style.borderColor = 'salmon';
      })
      backToTop.firstChild.addEventListener('mouseout', function(){
        this.style.backgroundColor = 'lightskyblue';
        this.style.color = 'white';
        this.style.borderColor = 'navy';
      })

      const p = backToTop.querySelector('p');
      p.style.color = 'currentcolor'
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

          const nav = document.querySelector('.navbar');
          const as = nav.querySelectorAll('a');
          for (let a of as) {
              const button = a.parentElement
              if (a.textContent === 'About Winston') {
                  a.classList.add("selected")
                  button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
              }
              else {
                  a.classList.remove("selected");
                  a.style.color = 'initial';
                  button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
              }
          }





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
