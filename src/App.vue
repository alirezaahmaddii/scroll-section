<template>
  <article class="content">
    <div  class=" inline-photo show-on-scroll">
    <img src="/media/image/pexels-francesco-ungaro-1525041.jpg"  class=" inline-photo show-on-scroll">
    </div>
    <div  class=" inline-photo show-on-scroll">
      <img src="/media/image/pexels-francesco-ungaro-1525041.jpg"  class=" inline-photo show-on-scroll">
    </div>
    <div  class=" inline-photo show-on-scroll">
      <img src="/media/image/pexels-francesco-ungaro-1525041.jpg"  class=" inline-photo show-on-scroll">
    </div>
    <div  class=" inline-photo show-on-scroll">
      <img src="/media/image/pexels-francesco-ungaro-1525041.jpg"  class=" inline-photo show-on-scroll">
    </div>
    <div  class=" inline-photo show-on-scroll">
      <img src="/media/image/pexels-francesco-ungaro-1525041.jpg"  class=" inline-photo show-on-scroll">
    </div>

    
  </article>




</template>
<script>
import Aos from 'aos' ;
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger.js';
import 'gsap/ScrollToPlugin';
import CSSRulePlugin from 'gsap/CSSRulePlugin'
export default {
  data: () => ({}),
  methods: {
    scr() {
// Detect request animation frame
      var scroll = window.requestAnimationFrame ||
          // IE Fallback
          function(callback){ window.setTimeout(callback, 1000/60)};
      var elementsToShow = document.querySelectorAll('.show-on-scroll');

      function loop() {

        Array.prototype.forEach.call(elementsToShow, function(element){
          if (isElementInViewport(element)) {
            element.classList.add('is-visible');
          }
          else {
            element.classList.remove('is-visible');
          }
        });

        scroll(loop);
      }

// Call the loop for the first time
      loop();

// Helper function from: http://stackoverflow.com/a/7557433/274826
      function isElementInViewport(el) {
        // special bonus for those using jQuery
        if (typeof jQuery === "function" && el instanceof jQuery) {
          el = el[0];
        }
        var rect = el.getBoundingClientRect();
        return (
            (rect.top >= -2500
                && rect.bottom <= 0)
            ||
            (rect.bottom >= (window.innerHeight || document.documentElement.clientHeight) &&
                rect.top <= (window.innerHeight || document.documentElement.clientHeight))
            ||
            (rect.top >= 0 &&
                rect.bottom <= (window.innerHeight || document.documentElement.clientHeight))
        );
      }
    },


  },
  mounted() {
 this.scr();
  }
}
</script>

<style lang="scss">
body *{
  background-color: black;
}
.inline-photo {
  //transform: translateY(4em) rotateZ(-5deg);
  transition: transform 4s .25s cubic-bezier(0,1,.3,1),
  opacity .3s .25s ease-out;
  width: 100%;
  will-change: transform, opacity;
  transform: translateY(-10%) scale(1) rotate3d(1,0,0,-60deg);
  opacity: 0;
}
//from to   1  ---- >   2
.inline-photo.is-visible {
  transform: translateY(0) scale(1);
  opacity: 1;

}

header {
  opacity: 0;
  transition: opacity .5s .25s ease-out;
}
header.is-visible {
  opacity: 1;
}

.main-photo {
  transform: scale(.8);
}

.heading {
  transform: translate(-50%, calc(-50% + 1em));
}

.is-visible .main-photo {
  transform: none;
}

.is-visible .heading {
  transform: translate(-50%, -50%);
}

.main-photo,
.heading {
  transition: transform 4s .25s cubic-bezier(0,1,.3,1),
  filter 10s 2s ease-out;
  will-change: transform;
}


</style>

<!--//active-->
<!--transform: translateY(0) scale(1);-->
<!--unactive-->
<!--transform: translateY(-80%) scale(1) rotate3d(1,0,0,-60deg);-->
<!--    opacity: 0;-->