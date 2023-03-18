<template>

  <div id="about" @mouseover="mouseOver()">
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
  title="https://www.linkedin.com/in/winston-lau/" @click="redirect($event)"><i class="bi bi-linkedin"></i></b-button>
  <b-button variant="outline-primary" title="https://github.com/loudringphone/" @click="redirect($event)"><i class="bi bi-github"></i></b-button>
  <b-button variant="outline-primary" title="copy to clipboard:0422882062" @click="copyMobile()"><i class="bi bi-phone"></i></b-button>
  <toast ref="toast" />

  <div class='footnote'>
    <p>Oh by the way, if you are browsing my portfolio in desktop mode, you can enlarge the gifs by clicking on them!</p>
  </div>

  <div id="notification">Redirect to <a href="https://www.linkedin.com/in/winston-lau/" target="_blank">https://www.linkedin.com/in/winston-lau/</a> in <span>5 seconds</span>. <br> Click the notification bar to abort the redirection.</div>
  </div>

</template>

<script>



export default {
  
  name:  'aboutwinston',
  data: function() {
            return {
                title: 'About Winston',
                features: [
                  {image:require('@/assets/about/graduation.jpeg'), alt:"This is me at the graduation ceremony for my accounting degree. I didn't know I would create a portfolio as a web developer one day!"}],
                isRedirecting: false
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
    redirect(event) {
      if (this.isRedirecting === false) {
        this.$toast.clear();
        this.isRedirecting = true;
        let button = event.target;
        if (button.children.length === 0) {
          button = button.parentElement;
        }
        const notification = document.querySelector('#notification');
        const a = notification.querySelector('a');
        a.href = button.title;
        a.textContent = button.title;
        const span = notification.querySelector('span');
        span.textContent = '5 seconds'
        notification.style.display = 'block';
        notification.style.opacity = 0;
        let opacity = 0;
        let gettingOpaque = setInterval(() => {
          opacity += 0.1;
          notification.style.opacity = opacity;
          if (opacity >= 1) {
            clearInterval(gettingOpaque);
          }
        }, 50);
        
        

        let countdown = setInterval(() => {
          if (span.textContent === '5 seconds') {
            span.textContent = '4 seconds';
          }
          else if (span.textContent === '4 seconds') {
            span.textContent = '3 seconds';
          }
          else if (span.textContent === '3 seconds') {
            span.textContent = '2 seconds';
          }
          else if (span.textContent === '2 seconds') {
            span.textContent = '1 second';
          }
          else if (span.textContent === '1 second') {
            span.textContent = '0 seconds';
          }
          else if (span.textContent === '0 seconds') {
            clearInterval(countdown);
            this.isRedirecting = false;
            window.location.assign(button.title);
          }
        }, 1000);
        notification.addEventListener('click', () => {
          this.isRedirecting = false;
          clearInterval(countdown);
          opacity = 1
          let gettingTransparent = setInterval(() => {
          opacity -= 0.1;
          notification.style.opacity = opacity;
          if (opacity <= 0) {
            clearInterval(gettingTransparent);
            notification.style.display = 'none'
          }
        }, 50);
        })
      }
    },
    copyMobile() {
      if (this.isRedirecting === false) {
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
  .footnote {
    justify-content: center;
    display: flex;
    width: 80%;
    margin-top: 50px;
  }
  .footnote > p {
    text-align: left;
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

  #notification {
    position: fixed;
    bottom: 0px;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 100;
    background-color: orange;
    color: aliceblue;
    padding: 12px;
    border-radius: 10px;
    cursor: pointer;
    line-height: 200%;
    display: none;
    opacity: 0;
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
    .footnote {
    margin-top: 50px;
    width: 85%;
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

    #notification {
    line-height: 150%;
    width: 100%;
    border-radius: 0px;
  }
  }
</style>
