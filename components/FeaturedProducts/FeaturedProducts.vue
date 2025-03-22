<template>
  <div class="root">
    <title-main align="center" primary="Featured" secondary="Products" />
    <div class="carousel-wrap">
      <v-btn class="nav prev" @click="slickPrev">
        <v-icon>mdi-arrow-left</v-icon>
      </v-btn>
      <v-btn class="nav next" @click="slickNext">
        <v-icon>mdi-arrow-right</v-icon>
      </v-btn>
      <div v-if="loaded">
        <splide
          ref="slider"
          :options="slickOptions"
        >
          <splide-slide
            v-for="(item, index) in dataProducts"
            :key="index"
          >
            <div class="item">
              <simple-thumb-card
                :title="item.title"
                :price="item.price"
                :img="item.img"
              />
            </div>
          </splide-slide>
        </splide>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './featured-style.scss';
</style>

<script>
import { Splide, SplideSlide } from '@splidejs/vue-splide';

import Title from '../Title';
import SimpleThumbCard from '../Cards/SimpleThumb';

const dataProducts = [
  {
    title: 'Ladies leather jacket',
    price: 'Ksh 1,500.00',
    img:'/products/image7.jpg',

  },
  {
    title: 'Mens Two piece set',
    price: 'Ksh 2,000.00',
    img: '/products/image.png',
  },
  {
    title: 'Mens Hoodie Set',
    price: 'Ksh 3,500.00',
    img: '/products/image2.jpg',
  },
  {
    title: 'Leather Jacket',
    price: 'Ksh 4,800.00',
    img: '/products/image4.jpg',
  },
  {
    title: 'Ladie TurtleNeck Sweater',
    price: 'Ksh 1000.00',
    img: '/products/image5.jpg',
  },
  {
    title: 'Short sleeve polo',
    price: 'Ksh 840.00',
    img: '/products/image6.jpg',
  },
  {
    title: '3 piece ladies stipped pants',
    price: 'Ksh 1,200.00',
    img: '/products/image8.jpg',
  },
  {
    title: 'Mens Two piece set',
    price: 'Ksh 900.00',
    img: '/products/image2.jpg'
  },
];

export default {
  components: {
    'title-main': Title,
    Splide,
    SplideSlide,
    SimpleThumbCard,
  },
  data() {
    return {
      loaded: false,
      dataProducts,
      slickOptions: {
        pagination: true,
        arrows: false,
        speed: 500,
        perPage: 6,
        perMove: 1,
        autoplay: true,
        interval: 7000,
        direction: 'ltr',
        breakpoints: {
          1024: {
            perPage: 4,
            type: 'loop',
          },
          600: {
            perPage: 2,
          },
        },
      },
    };
  },
  mounted() {
    this.loaded = true;
    setTimeout(() => {
      if (this.$vuetify.locale.isRtl) {
        this.slickOptions.direction = 'rtl';
      } else {
        this.slickOptions.direction = 'ltr';
      }
    }, 100);
  },
  methods: {
    slickNext() {
      this.$refs.slider.go('>');
    },
    slickPrev() {
      this.$refs.slider.go('<');
    },
  },
};
</script>