<template>

  <div id="aboutwinston" @mouseover="mouseOver()">
    <h2>{{ title }}</h2>
    <br>
    <h3>Hello! I'm a web developer based in Sydney!</h3>
    <br><br>
    <div class='profile'>
      <p class='para1'>
        I recently graduated from General Assembly where I learned about both front and back end development. I was an accountant previously and I have want to change my career for a long time. Finally I have commited myself in a 12 week intensive course at GA and it is the second best decision I have made in my life. (The best one is of course coming to Australia! )
      </p>

      <figure id='winston'>
        <img :src='features[0].image'  :alt="features[0].alt">
        <figcaption>{{features[0].alt}}</figcaption>
      </figure>

      <br>
    <p class='para2' >I consider myself a creative and curious person. If you like my below works and ideas, please do not hesitate to contact me and discuss any career opportunities!</p>
    </div>
    

  <b-button variant="outline-primary" title="mailto:wingfunglau@gmail.com" @click="mailTo()"><i class="bi bi-envelope"></i></b-button>
  <b-button variant="outline-primary" 
  title="https://www.linkedin.com/in/winston-lau/" @click="openLinkedin()"><i class="bi bi-linkedin"></i></b-button>
  <b-button variant="outline-primary" title="https://github.com/loudringphone/" @click="openGithub()"><i class="bi bi-github"></i></b-button>
  <b-button variant="outline-primary" title="copy to clipboard:0422882062" @click="copyMobile()"><i class="bi bi-phone"></i></b-button>
  <toast ref="toast" />

  </div>

</template>

<script>



export default {
  
  name:  'aboutwinston',
  data: function() {
            return {
                title: 'About Winston',
                features: [
                  {image:require('@/assets/about/graduation.jpeg'), alt:"This is me at the graduation ceremony for my accounting degree. I didn't know I would create a portfolio as a web developer one day!"}]
            };
        },
  methods: {
    mouseOver() {
      const nav = document.querySelector('nav')
      const buttons = nav.querySelectorAll('button')
      for (let button of buttons) {
        button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
        button.firstChild.classList.remove("selected")
        if (button.firstChild.textContent === 'About Winston') {
          button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
          button.firstChild.classList.add("selected")
        }
      }
    },
    mailTo() {
      window.location.href = "mailto:wingfunglau@gmail.com";
    },
    openLinkedin() {
      window.open("https://www.linkedin.com/in/winston-lau/", "_blank");
    },
    openGithub() {
      window.open("https://github.com/loudringphone/", "_blank");
    },
    copyMobile() {
      const number = '0422882062';

      const tempInput = document.createElement('input');
      tempInput.value = number;
      document.body.appendChild(tempInput);

      tempInput.select();
      document.execCommand('copy');

      document.body.removeChild(tempInput);

      this.$toast.info(`${number} has been copied to the clipboard!`, {
        position: "bottom-center",
        timeout: 3000,
        closeOnClick: true,
        pauseOnFocusLoss: true,
        pauseOnHover: true,
        draggable: true,
        draggablePercent: 0.6,
        showCloseButtonOnHover: false,
        hideProgressBar: true,
        closeButton: "",
        icon: true,
        rtl: false
      });
    }
    
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  
  * {
    overflow-x: hidden;
  }
  .profile {
    justify-content: center;
    width: 80%;
    display: grid;
    grid-template-columns: repeat(2, 380px);
    grid-template-rows: repeat(2, auto);
    gap: 35px
  }

  p.para1 {
    
    text-align: left;
    line-height: 200%;
    grid-column: 2;
    grid-row: 1;
  }


  figure {
    width: 380px;
    grid-column: 1;
    grid-row: 1;
    justify-self: right
  }
  img {
    width: 380px !important;
  }
  
  figcaption {
    text-align: left;
    width: 100%;
    margin-top: 15px;
    font-size: small;
  }

  p.para2 {
    grid-column: span 2;
    grid-row: 2;
    text-align: left;
  }
  button.btn.btn-outline-primary {
    background-color: lightyellow;
    color: salmon;
    border-color: salmon;
    border-left-width: thick;
    border-bottom-width: thick;
    border-radius: 10px;
    margin: 0 10px 0 10px;
  }

  button.btn.btn-outline-primary:hover {
    background-color: lightskyblue;
    color: white;
    border-color: navy;
    
  }

  button.btn.btn-outline-primary:click {
    color:red;
  }
  button.btn.btn-outline-primary:active {
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

  ::before {
    font-size: xxx-large;
  }

 
  @media (max-width: 1000px) {
    h3 {
      width: 90%;
    }
    .profile {
      display: block;
      max-height:max-content;
      text-align: -webkit-center;
      margin-bottom: 50px;
      width: 85%
    }
   
    figure {
      margin-top: 45px;
      width: 450px;
    }
    
    img {
      width: 450px !important;
    }

    ::before {
    font-size: xx-large;
  }
  }
</style>
