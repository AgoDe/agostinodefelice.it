<template>
  <div id="app">

      
    <section class="all_display init_section">

        <div class="container h-100">
          <div class="row align-items-center h-100 ">
            <div class="col-12 text-center init_box">

              <h3 class="init_an">scroll to start</h3>

              <div class=" init_an chevron_box">
                <i class="icon-pixel-down"></i>
                <i class="icon-pixel-down mt-3"></i>
              </div>

              <h1 class="title_an">agostino de felice</h1>
              <h3 class="title_an">full stack web developer</h3>

              <div class="second chevron_box">
                  <i class="icon-pixel-down"></i>
                  <i class="icon-pixel-down mt-3"></i>
              </div>
              
            </div>

          </div>

        </div>

      </section>

  
  </div>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);


export default {
  name: 'App',
  components: {
    
  },
  data(){
    return{

    }
  }, // end of data
  mounted(){

    this.initAnimation();
  }, // end of mounted
  methods: {
    initAnimation: function(){
      let initTl = gsap.timeline({
        scrollTrigger: {
          trigger: '.init_section',
          end: '+=700',
          scrub: 5,
          markers: true,
          pin: '.init_section',
        },
        ease: "power4.out"
      });

      initTl
      .to('.init_an', { y: () => - window.innerHeight})
      .from('.title_an', {y: () => window.innerHeight, opacity: 0, stagger: 0.2})
      .to('.init_box', {border: '5px solid #eac817', duration: 2})
      .from('.second.chevron_box', {y: () => window.innerHeight, opacity: 0, delay: 0.3})

    }
  }, // end of methods

}
</script>

<style lang="scss">
@import 'src/styles/main.scss';
 
 .init_section {

  .init_box {
    display: flex;
    justify-content: center;
    flex-direction: column;
    height: 60%;
    border: 5px solid transparent;
    border-radius: 15px;

    h1.title_an {
      font-size: 35px;
      letter-spacing: 8px;
      opacity: 1;
      margin-bottom: 30px;

    }
    h3.title_an {
      color: white;
      font-size: 20px;
      letter-spacing: 2px;
      opacity: 1;
    }
  }

 }
</style>
