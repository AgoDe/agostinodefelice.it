<template>
<div class="">

    <section class="all_display welcome_container">

        <div class="container h-100">
            <div class="row h-100 align-items-center">

                <div class="col-12 text-center welcome_box">
                    <h3 class=" welcome_animation">scroll to start</h3>
                    <i class="icon-pixel-down welcome_animation"></i>
                    <i class="icon-pixel-down mt-3 welcome_animation"></i>
                </div>
                
            </div>
        </div>
       
    </section>
    <!-- end of welcome_container -->

    <section class="all_display title_container">

        <div class="pacman_box_in">
            
            <div class="ghost"></div>

            <div class="pacman">
                <div class="mouth_dx"></div>
            </div>
        </div>

        <div class="container h-100">

            <div class="row h-100 align-items-center">
                <div class="col-12 title_box text-center">
                    <h1>agostino de felice</h1>
                    <h3>full stack web developer</h3>
                </div>
             
            </div>
        </div>

          <div class="pacman_box_out">
            
            <div class="vulnerable_ghost"></div>

            <div class="pacman">
                <div class="mouth_sx"></div>
            </div>
        </div>


    </section>
    <!-- end of title_container -->
</div>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);


export default {
    data(){
        return {
            PacmanVel: 650,
        }
    }, // end of data
    mounted(){

        this.pacmanAnimation();

    }, // end of mounted
    methods: {
        pacmanAnimation: function() {
            console.log(window.innerWidth)

            // pacman in entrata
            gsap.to('.prova', {
                
                scrollTrigger: {
                    trigger: '.prova_box',
                    markers: false,
                    toggleActions: 'restart pause resume resume',
                    
                },
                x: () => window.innerWidth + 200,
                duration: window.innerWidth / this.PacmanVel,
                ease: 'linear',
                
            })

            // pacman in uscita

            gsap.to('.pacman_box_out', {
                
                scrollTrigger: {
                    trigger: '.title_container',
                    start: 'bottom 80%',
                    end: 'bottom top',
                    markers: false,
                    toggleActions: 'restart pause resume resume',
                    
                },
                x: () => - window.innerWidth -300,
                duration: window.innerWidth / this.PacmanVel,
                ease: 'linear',
                
            })

            // animazione titoli in entrata
            gsap.fromTo('.title_box h1',
                {
                    x: () => window.innerWidth,
                }, 
                {
                    scrollTrigger: {
                        scrub: 5,
                        trigger: '.title_container',
                        start: 'top 65%',
                        end: 'center center',
                        markers: false,
                        id: 'ingresso',
                    },
                    x: 0, 
                })
            gsap.fromTo('.title_box h3',
                {
                    
                    x: () => - window.innerWidth,
                }, 
                {
                    scrollTrigger: {
                        scrub: 5,
                        trigger: '.title_box',
                        end: '+=600',
                    },
                    x: 0,
                })

            // animazioni titoli in uscita
            gsap.fromTo('.title_box h1', 
            {
                x: 0
            },
            {
                scrollTrigger: {
                        scrub: 3,
                        trigger: '.title_container',
                        start: 'bottom 80%',
                        end: 'bottom top',
                        markers: false,
                        id: 'uscita',
                    },
                x: () => - window.innerWidth - 100,
                
            })
            gsap.fromTo('.title_box h3', 
            {
                x: 0
            },
            {
                scrollTrigger: {
                        scrub: 3,
                        trigger: '.title_container',
                        start: 'bottom 80%',
                        end: 'bottom top',
                        markers: false,
                        id: 'uscita',
                    },
                x: () => window.innerWidth + 100,
                
            })
          
          
        }
    }, // end of methods

}
</script>

<style lang="scss">
@import 'src/styles/main.scss';

    .welcome_container {
        
        .col-12 {
            position: relative;   
            
            h3 {
                text-transform:capitalize;
            }
            .icon-pixel-down {
                animation-name: chevron_down;
                animation-duration: 850ms;
                animation-iteration-count: infinite;
                animation-timing-function: steps(4, end);
                left: 50%;
                transform: translate(-50%, 0);
            }
        }
    } // end of welcome_container

    .title_container {
        position: relative;
        .pacman_box_in {
            position: absolute;
            top: 200px;
            left: -200px;
           
            .pacman {
                position: absolute;
                top: 0;
                margin-left: 100px;
            }
        }

        .title_box {
            h1 {
                font-size: 30px;
                text-transform: capitalize;
                margin-bottom: 30px;
                letter-spacing: 5px;
            }   
            h3 {
                color: white;
                font-size: 20px;
                text-transform: capitalize;
                letter-spacing: 2px;

            }
        }

         .pacman_box_out {
            position: absolute;
            bottom: 200px;
            right: -200px;
           
            .pacman {
                position: absolute;
                top: 0;
                margin-left: 100px;
            }
        }
        
    }




</style>