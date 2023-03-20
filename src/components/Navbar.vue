<template>

  <nav id="navbar" class="navbar navbar-expand-lg navbar-light bg-light" @mouseover="gettingOpaque($event)">
    <i class="bi bi-list" @click="toggleNavbar($event)"></i>
    <button class="btn btn-block btn-lg glow-button btn-warning"><a class="selected" href="about" @click="scrollTo($event)">About Winston</a></button>
    <button v-for="(nav, i) in navs" :key="i">
      <a :href="nav.href" @click="scrollTo($event)">{{nav.text}}</a>
    </button>
</nav>

</template>

<script>
export default {
  name:  'NavbarComponent',
  data: function() {
            return {
                navs: [
                    { text: 'Ultimate Tic-tac-toe', href: 'uttt'},
                    { text: 'Sancbook', href: 'sancbook'},
                    { text: '3Lancers', href: '3lancers'},
                    { text: 'Tutonet', href: 'tutonet'}
                ]
            };
        },
  methods: {
    gettingOpaque(event){
      const nav = event.target;
      nav.style.opacity = 1;
      const navbar = document.querySelector('#navbar');
      navbar.style.borderBottom = 'groove';
      if (window.innerWidth <= 1000) {
        navbar.style.borderRight = 'groove';
      };
    },
    toggleNavbar(event){
      const hamburger = event.target;
      const nav = hamburger.parentElement;
      nav.classList.toggle('expanded');
      if (nav.classList.contains('expanded')) {
        nav.style.opacity = 1;
      };
      
    },
    scrollTo(event){
      event.preventDefault();
      const a = event.target;
      const nav = a.parentElement.parentElement
      // nav.classList.remove('expanded')
      const as = nav.querySelectorAll('a')
      const button = a.parentElement
      const buttons = nav.querySelectorAll('button')
      for (let a of as) {
        a.classList.remove("selected")
        a.style.color = 'initial'
      }
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
      }
      button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
      a.classList.add("selected")
      const h2s = document.querySelectorAll('h2');
      for (let h2 of h2s) {
        if (h2.textContent === event.target.textContent) {
          
          document.body.style.pointerEvents = "none";
          
          h2.parentElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
          function preventDefault(e) {
  e.preventDefault();
}
          window.addEventListener("wheel", preventDefault, { passive:false })
          let scrolling = setInterval(() => {
            if (Math.floor(h2.parentElement.getBoundingClientRect().top) <= 10 && Math.floor(h2.parentElement.getBoundingClientRect().top) >= -10) {
              window.removeEventListener("wheel", preventDefault, { passive:false });
              document.body.style.pointerEvents = "auto";
              clearInterval(scrolling);
}
          }, 200);
          
          
          
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#navbar {
    position: fixed;
    top: 0;
    width: 100vw;
    height: 50px;
    z-index: 99;
    padding-right: 15vw;
    padding-left: 15vw;
    place-content: space-between;
      }
#navbar > button {
    margin-bottom: 0;
    height:fit-content;
    font-size: medium;
    border: none;
    background-color: transparent;
    /* width: 200px; */
}

#navbar > button:hover {
  border: groove;
  border-radius: 10px;
  border-width: medium;
  border-color: aliceblue;
}

  #navbar > button.glow-button:hover {
  border: none;
  }
.glow-button {
    box-shadow: 0 0 15px var(--box-shadow-color);
    --box-shadow-color: #ffc107;
    background-color: #ffc107 !important;
    font-size: medium;
    height: 30px;
    overflow: hidden;
    padding: 0 10px 0 10px;
}
#navbar > button > a {
    text-decoration: none;
    color: black;
}
a.selected {
  color: white !important;
}

@media (max-width: 1000px) {

#navbar > button:hover {
  border: none;
}
}
</style>
