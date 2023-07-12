<template>

  <div id="about" @mouseover="mouseOver()" @touchstart="touchStart()">
    <h2>{{ title }}</h2>
    <h3>Hello! I'm a junior software developer based in Sydney!</h3>
    <br>
    <b-button variant="outline-primary" title="Winston's Resume" @click="redirect($event)"><p>RESUME</p><i class="bi bi-file-person"></i></b-button>
    <b-button variant="outline-primary" title="mailto:wingfunglau@gmail.com" @click="mailTo()"><p>EMAIL</p><i class="bi bi-envelope"></i></b-button>
    <b-button variant="outline-primary" 
    title="Winston's Linkedin" @click="redirect($event)"><p>LINKEDIN</p><i class="bi bi-linkedin"></i></b-button>
    <b-button variant="outline-primary" title="Winston's Github" @click="redirect($event)"><p>GITHUB</p><i class="bi bi-github"></i></b-button>
    <b-button variant="outline-primary" title="copy to clipboard:0422882062" @click="copyMobile()"><p>MOBILE</p><i class="bi bi-phone"></i></b-button>
    <br><br><br>
    <div class='profile'>
      <p class='para1'>
        I have recently graduated from General Assembly where I have learned about both front and back end development. I was an accountant previously and I have wanted to change my career for a long time. Finally I have committed myself in a 12 week intensive course at GA and it is the second best decision I have made in my life. (The best one is of course coming to Australia! )
      </p>

      <figure id='winston'>
        <img :src='features[0].image'  :alt="features[0].alt">
        <figcaption>{{features[0].alt}}</figcaption>
      </figure>

      <br>
    <p class='para2' >I consider myself a creative and curious person. If you like my below works and ideas, please do not hesitate to contact me and discuss any career opportunities!</p>
    </div>
    

  
  <toast ref="toast" />

  <div id="notification">Redirect to <a href="https://www.linkedin.com/in/winston-lau/" target="_blank">Winston's Linkedin</a> in <span>5 seconds</span>. <br> Click this notification bar to abort the redirection.</div>
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
    touchStart() {
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
      if (this.isRedirecting === false) {
        window.location.href = "mailto:wingfunglau@gmail.com";
      }
    },
    redirect(event) {
      if (this.isRedirecting === false) {
        this.$toast.clear();
        this.isRedirecting = true;
        let button = event.target;
        if (button.children.length === 0) {
          button = button.parentElement;
        }
        const about = document.querySelector('#about');
        const buttons = about.querySelectorAll('button')
        for (let b of buttons) {
          if (b != button) {
          b.style.pointerEvents = 'none';
          b.style.backgroundColor = 'lightgrey';
          b.style.color = 'grey';
          b.style.borderColor = 'grey';
          }
        }
        const notification = document.querySelector('#notification');
        const a = notification.querySelector('a');
        a.textContent = button.title;

        switch (button.title) {
          case "Winston's Resume":
            a.href = "https://www.canva.com/design/DAFbiIUVqv4/mdC-d-UCB2GMwpETVNAwSg/view?utm_content=DAFbiIUVqv4&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton";
            break;
          case "Winston's Linkedin":
            a.href = "https://www.linkedin.com/in/winston-lau/";
            break;
          case "Winston's Github":
            a.href = "https://github.com/loudringphone/";
            break;
        }
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
            window.location.assign(a.href);
          }
          else if (span.textContent === '0 seconds') {
            clearInterval(countdown);
            this.isRedirecting = false;
            for (let button of buttons) {
              button.style.pointerEvents = 'auto'
              button.style.backgroundColor = 'lightyellow';
              button.style.color = 'salmon';
              button.style.borderColor = 'salmon';
            }
            // window.location.assign(a.href);
          }
        }, 1000);
        notification.addEventListener('click', () => {
          this.isRedirecting = false;
          clearInterval(countdown);
          for (let button of buttons) {
            button.style.pointerEvents = 'auto'
            button.style.backgroundColor = 'lightyellow';
            button.style.color = 'salmon';
            button.style.borderColor = 'salmon';


            button.addEventListener('mouseover', () => {
              button.style.backgroundColor = 'lightskyblue';
              button.style.color = 'white';
              button.style.borderColor = 'navy';
            });
  
  

            button.addEventListener('mouseout', () => {
              button.style.backgroundColor = 'lightyellow';
              button.style.color = 'salmon';
              button.style.borderColor = 'salmon';
            });
          }
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
        this.$toast.clear();
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
  button {
    display: inline-flex;
    align-items: center;
    padding: 0;
    height: 75px;
    width: 75px;
    position: relative;
  }
  button > p {
    position: absolute;
    left: -20px;
    text-align: right;
    font-size: small;
    transform: rotate(-90deg);
    width: 60px;
  }
  .bi {
    position: absolute;
    top: 5.5px;
    right: 3px;
  }
  .bi-envelope {
    top: 1px;
  }
  .bi::before, [class^="bi-"]::before, [class*=" bi-"]::before {
    font-size: 48px;
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
    justify-self: right;
  }
  figure img {
    width: 380px;
    border-radius: 10px;;

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
      width: 90%
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

    button.btn.btn-outline-primary {
    margin: 0 3px 10px 3px;
  }

    #notification {
    line-height: 150%;
    width: 100%;
    border-radius: 0px;
  }

  @media (max-width: 600px) {
    #winston {
      width: 100% !important;
    }
    img {
      width: 100% !important;
    }



  }
  }
</style>
