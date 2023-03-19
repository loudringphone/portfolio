<template>
  <div>
    <AboutWinston />
    <Navbar />
    <Uttt />
    <Sancbook />
    <Threelancers />
    <Tutonet />
    <BackToTop />
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from '@/components/Navbar.vue'
import AboutWinston from '@/components/AboutWinston.vue'
import Uttt from '@/components/Uttt.vue'
import Sancbook from '@/components/Sancbook.vue'
import Threelancers from '@/components/Threelancers.vue'
import Tutonet from '@/components/Tutonet.vue'
import BackToTop from '@/components/BackToTop.vue'



let gettingOpaque

export default {
  name: 'HomeView',
  components: {
    Navbar,
    AboutWinston,
    Uttt,
    Sancbook,
    Threelancers,
    Tutonet,
    BackToTop
  },
  mounted () {
    window.addEventListener('scroll', function() {
       const nav = this.document.querySelector('.navbar')
       nav.style.opacity = 0.35;
       if (window.innerWidth > 1000) {
        nav.style.border = 'none'
      }
       
        
        if (gettingOpaque) {
    clearTimeout(gettingOpaque);
  }

  gettingOpaque = setTimeout(function() {
    nav.style.opacity = 1;
    if (window.innerWidth > 1000) {
        nav.style.borderBottom = 'groove'
    }
  }, 3500);
    });
  },
}
</script>

<style>
* {
    position: relative;
    overflow: overlay;
    margin: auto;
    text-align: center;
    font-family: Arial, Helvetica, sans-serif;
}
.navbar {
    border-bottom: groove;
}
h2 {
    text-align: center;
    padding-top: 20px;
    padding-bottom: 20px;
}
.grid-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 1fr);
    gap: 20px;
    width: max-content;
    position:relative;
}
.image-container {
    position: relative;
    display: inline-block;
    position: relative;
    overflow: hidden;
    border-radius: 15px;
}

.close-btn {
    position: absolute;
    margin-top: 20%;
    right: 5%;
    height:fit-content;
    background-color: transparent;
    border: none;
    color: ivory;
    font-size: 80px;
    display: none;
    cursor: pointer;
    z-index: 1;
}
p.esc {
    color: white ;
    text-align: center;
    font-size: large;
}
.enlarged {
    position: absolute;
    justify-self: center;
    margin-left: 5%;
    margin-top: 5%;
    z-index: 1;
    border-radius: 15px;
    box-shadow: 0 0 30px var(--box-shadow-color);
    --box-shadow-color: white;
    overflow: hidden;
}
.uttt.enlarged {
    height: 490px;
}
.sancbook.enlarged {
    height: 725px;
}
.tutonet.enlarged {
    height: 485px;
}
#about {
    background-color: lightcyan;
    min-height: 100vh;
    padding: 50px 0 50px 0;
}
#uttt {
    background-color: #DCDCF5;
    min-height: 100vh;
    padding: 50px 0 50px 0;
}
.uttt {
    cursor: pointer;
}
#sancbook {
    background-color: #FEF0E8;
    min-height: 100vh;
    padding: 50px 0 50px 0;
}
.sancbook {
    cursor: pointer;
}
#threelancers {
    background-color: #DCF5DC;
    min-height: 100vh;
    padding: 50px 0 50px 0;
}
.threelancers {
    cursor: pointer;
}
#tutonet {
    background-color: #ffd7de;
    min-height: 100vh;
    padding: 50px 0 50px 0;
}
.tutonet {
    cursor: pointer;
}

#backToTop {
    background-color: gainsboro;
    padding-bottom: 25px;
}
h2, p {
    margin-bottom: 0 !important;
}
ul {
    list-style-type: square !important;
    list-style: inside;
    display: inline-flex;
    width: 80%;
    padding-left: 0 !important;
    margin-top: 20px !important;
    margin-left: 15px;
    margin-right: 15px;
    margin-bottom: 25px !important;
}
.bi-list {
    display: none;
}


@media (max-width: 1000px) {
    * {
        position: relative;
    }
    .bi-list {
        display: block;
        margin-left: 5.5px;
        
        cursor: pointer;
        font-size: xx-large;
    }
    .navbar {
        opacity: 0.35;
        width: 65px !important;
        padding-right: 1vw !important;
        padding-left: 1vw !important;
        height: auto !important;
        border-style: groove;
        border-bottom-right-radius: 10px;
        transition: width 1s;
        
    }
    .navbar > button {
        display: none;
    }
    
    .navbar:hover {
        opacity: 1;
    }
    .navbar.expanded {
        opacity: 1;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: left;
        width: 200px !important;
        padding-bottom: 20px;
        font-size: small;
        line-height: 250%;
    }
    .navbar.expanded > button {
        margin-left: 0px;
        margin-right: 0px;
        margin-top: 20px;
        display: block;
    }




    ul {
        display: block;
    }
    li {
        text-align: left;
        margin-left: 25%;
    }
    .grid-container {
        display: block;
        

    }
    img {
        width: 90vw;
    }
    .image-container {
        margin-bottom: 20px;
    }
    #aboutwinston {
    padding: 25px 0 50px 0;
    }
    #uttt {
    padding: 25px 0 25px 0;
    }
    #sancbook {
    padding: 25px 0 25px 0;
    }
    #threelancers {
    padding: 25px 0 25px 0;
    }
    #tutonet {
    padding: 25px 0 25px 0;
    }
    .uttt {
        cursor: default;
    }
    .sancbook {
        cursor: default;
    }
    .threelancers {
        cursor: default;
    }
    .tutonet {
        cursor: default;
    }




}
</style>
