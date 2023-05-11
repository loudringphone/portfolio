<template>
  <div>
    <AboutWinston />
    <Navbar />
    <Videostore />
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
import Videostore from '@/components/Videostore.vue'
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
    Videostore,
    Uttt,
    Sancbook,
    Threelancers,
    Tutonet,
    BackToTop
  },
  mounted () {
    window.addEventListener('touchend', function() {
            const about = this.document.querySelector('#about')
            const nav = this.document.querySelector('.navbar');
            const isExpanded = nav.classList.contains('expanded')
            let now;
            let then = Infinity;
            let scrolling = setInterval(() => {
                now = about.getBoundingClientRect().bottom
                // if (now === then) {
                //     clearInterval(scrolling);
                    let selected;
                    let bottom = Infinity;
                    const videostore = this.document.querySelector('#videostore')
                    const uttt = this.document.querySelector('#uttt')
                    const sancbook = this.document.querySelector('#sancbook')
                    const threelancers = this.document.querySelector('#threelancers')
                    const tutonet = this.document.querySelector('#tutonet')
                    if (about.getBoundingClientRect().bottom >= 400) {
                        if (about.getBoundingClientRect().bottom < bottom) {
                                selected = 'About Winston';
                                bottom = about.getBoundingClientRect().bottom;
                            }
                    };
                    if (videostore.getBoundingClientRect().bottom >= 400) {
                        if (videostore.getBoundingClientRect().bottom < bottom) {
                                selected = 'Ultimate Tic-tac-toe';
                                bottom = videostore.getBoundingClientRect().bottom;
                            }
                    };
                    if (uttt.getBoundingClientRect().bottom >= 400) {
                        if (uttt.getBoundingClientRect().bottom < bottom) {
                                selected = 'Ultimate Tic-tac-toe';
                                bottom = uttt.getBoundingClientRect().bottom;
                            }
                    };
                    if (sancbook.getBoundingClientRect().bottom >= 400) {
                        if (sancbook.getBoundingClientRect().bottom < bottom) {
                                selected = 'Sancbook';
                                bottom = sancbook.getBoundingClientRect().bottom;
                            }
                    };
                    if (threelancers.getBoundingClientRect().bottom >= 400) {
                        if (threelancers.getBoundingClientRect().bottom < bottom) {
                                selected = '3Lancers';
                                bottom = threelancers.getBoundingClientRect().bottom;
                            }
                    };
                    if (tutonet.getBoundingClientRect().bottom >= 400) {
                        if (tutonet.getBoundingClientRect().bottom < bottom) {
                                selected = 'Tutonet';
                                bottom = tutonet.getBoundingClientRect().bottom;
                            }
                    };
                    const as = nav.querySelectorAll('a');
                    for (let a of as) {
                        const button = a.parentElement
                        if (a.textContent === selected) {
                            a.classList.add("selected")
                            button.classList.add("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
                        }
                        else {
                            a.classList.remove("selected");
                            a.style.color = 'initial';
                            button.classList.remove("btn", "btn-block", "btn-lg", "glow-button", "btn-warning")
                        }
                    }
                if (now === then) {
                    clearInterval(scrolling);
                    setTimeout(() => {
                            if (isExpanded) {
                                nav.classList.remove('expanded');
                                nav.style.opacity = 0.35;
                            }
                    }, 150);
                }
                then = now
            }, 275);
    });


    let lastScrollTop = 0;

    window.addEventListener('scroll', function() {
       const nav = this.document.querySelector('.navbar');
       if (!nav.classList.contains('expanded')) {
        // nav.style.opacity = 0.35;
       }
       if (window.innerWidth > 1000) {
        nav.style.border = 'none'
       }
       if (gettingOpaque) {
        clearTimeout(gettingOpaque);
       }
        gettingOpaque = setTimeout(function() {
            nav.style.opacity = 1;
        }, 3500);

        
        let st = window.pageYOffset || document.documentElement.scrollTop;
        if (st > lastScrollTop) {
            if (!nav.classList.contains('expanded')) {
                nav.style.opacity = 0.35;
            }
            // downscroll code
        } else if (st < lastScrollTop) {
            nav.style.opacity = 1;
        } // else was horizontal scroll
        lastScrollTop = st <= 0 ? 0 : st; // For Mobile or negative scrolling
        




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
    display: flex;
    box-shadow: inset 0 -6px 6px -6px rgba(0, 0, 0, 0.4);
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
.videostore.enlarged {
    height: max-content;
}
.videostore.enlarged img {
    height: 110%;
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
#videostore {
    background-color: #f3ffd9;
    min-height: 100vh;
    padding: 50px 0 50px 0;
}
.videostore {
    cursor: pointer;
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
        box-shadow: inset 0 -6px 6px -6px rgba(0, 0, 0, 0.6), inset -6px 0 6px -6px rgba(0, 0, 0, 0.6);

        opacity: 0.35;
        width: 65px !important;
        padding-right: 1vw !important;
        padding-left: 1vw !important;
        height: auto !important;
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
    #videostore {
    padding: 25px 0 25px 0;
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
    .videostore {
        cursor: default;
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
