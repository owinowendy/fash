<template>
  <div class="root">
    <v-container>
      <div class="slider-wrap">
        <transition-group
          :name="transition"
          tag="div"
        >
          <div
            v-for="number in [currentImg]"
            :key="number"
            class="slide slider-content"
          >
            <div class="inner item" :class="[ number % 2 ? 'even' : 'odd' ]">
              <div class="inner-bg">
                <v-row>
                  <v-col md="4" cols="12" class="pa-0">
                    <div class="text">
                      <hidden point="mdUp">
                        <div class="background">
                          <figure>
                            <img :src="content[Math.abs(currentImg) % content.length].image" alt="promotion">
                          </figure>
                        </div>
                      </hidden>
                      <h2 class="use-text-title">
                        <span class="use-text-subtitle2">
                          {{ $t('fashionLanding.promo_caption') }}
                        </span>
                        SALE
                      </h2>
                      <h4 class="use-text-subtitle">
                        {{ $t('fashionLanding.promo_title') }}
                      </h4>
                      <article class="desc">
                        <h6 class="use-text-paragraph">
                          {{ $t('fashionLanding.promo_desc') }}
                        </h6>
                      </article>
                      <v-btn variant="outlined" class="button">
                        {{ $t('fashionLanding.promo_btn') }}
                        <v-icon class="icon-btn">
                          mdi-arrow-right
                        </v-icon>
                      </v-btn>
                    </div>
                  </v-col>
                  <v-col md="8" cols="12" class="pa-0">
                    <hidden point="smDown">
                      <div class="image">
                        <figure>
                          <img :src="content[Math.abs(currentImg) % content.length].image" alt="promotion">
                        </figure>
                      </div>
                    </hidden>
                  </v-col>
                </v-row>
              </div>
            </div>
          </div>
        </transition-group>
      </div>
      <a
        href="javascript:void(0)"
        class="prev"
        @click="prev"
      >
        <v-icon class="arrow-icon">mdi-arrow-left</v-icon>
      </a>
      <a
        href="javascript:void(0)"
        class="next"
        @click="next"
      >
        <v-icon class="arrow-icon ">mdi-arrow-right</v-icon>
      </a>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './promotion-style.scss';
</style>

<script>
import Hidden from '../Hidden';
import screen1 from '@/assets/images/screen1.png';
import screen2 from '@/assets/images/screen2.png';
import screen3 from '@/assets/images/screen3.png';


;
const sliderData = [
  {image:screen1},
  {image:screen2},

  {image:screen3},

 

];

export default {
  components: {
    Hidden,
  },
  data() {
    return {
      content: sliderData,
      transition: '',
      autoplay: null,
      currentImg: 0,
    };
  },
  mounted() {
    this.playSlider();
  },
  beforeUnmount() {
    clearInterval(this.autoplay);
  },
  methods: {
    playSlider() {
      this.autoplay = setInterval(() => {
        this.currentImg += 1;
        this.transition = 'slide-right';
      }, 100000);
    },
    manualPlay() {
      clearInterval(this.autoplay);
      setTimeout(() => {
        this.playSlider();
      }, 1);
    },
    next() {
      this.manualPlay();
      this.currentImg += 1;
      this.transition = 'slide-right';
    },
    prev() {
      this.manualPlay();
      this.currentImg -= 1;
      this.transition = 'slide-left';
    },
    swipeLeft() {
      this.next();
    },
    swipeRight() {
      this.prev();
    },
  },
};
</script>
