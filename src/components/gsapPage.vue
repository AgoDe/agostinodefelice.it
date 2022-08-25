<template>
  <div class="hello container">

    <div class="row">
      <div class="col-12">

        <h1 class="title">GSAP test</h1>
  
         <div class="a box"></div>
  
        <div class="b box"></div>
  
        <div class="c box"></div>
      </div>

    </div>

  </div>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import Draggable from "gsap/Draggable";
import MotionPathPlugin from "gsap/MotionPathPlugin";

gsap.registerPlugin(ScrollTrigger, Draggable, MotionPathPlugin);
export default {
  name: 'gsap',
  props: {
   
  },
  mounted(){
    this.esempio();
  },
  methods: {
    esempio: function() {

        gsap.to('.title', {
          scrollTrigger: {
            trigger: '.a',
            start: 'top top',
            markers: true,
            endTrigger: '.c',
            end: 'bottom top',
            scrub: true,
            // pin: '.title',
            // pinSpacing: false,
                       // serve per bloccare l'elemento sulla stessa posizione nella viewport durante lo scorrimento
          },
          y: 1200,
        });

        gsap.to('.b', {
          scrollTrigger: {
            
            trigger: '.b',              // l'elemento in cui inizia l'animazione
            start: 'center center',     // indica quando iniziare l'animazione: 1° valore riferito all'elemento, il 2° alla viewport
            end: '+=400',               // default: bottom top // "+=300" per definire la durata dello scrolling
            // endTrigger: '.c',        // è possibile anche definire un elemento di fine
            markers: false,              // per attivare i markers per l'animazione
            scrub: true,                // true => scorre in parallelo con la rotella   // 1 => scorre con animazione rallentata (più armonico)
            // toggleActions: 'play none none none',   // le azioni che succedono allo scroll, valori possibili => play, pause, restart, reverse, reset, complete, none
                                                    // 1° valore => appena lo scroll tocca lo start-point
                                                    // 2° valore => appena lo scroll supera l'end-point
                                                    // 3° valore => l'azione che fa quando riprende l'animazione
                                                    // 4° valore => ? conviene mettere pause
          },
          x: 1000,






    })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import 'bootstrap';

  .hello {

    .box {
      margin-bottom: 500px;
      height: 150px;
      width:  150px;

    }
    .a {
      background: red;
    }
    .b {
    background: blue;
    }
    .c {
      background: green;
    }
  }
</style>
