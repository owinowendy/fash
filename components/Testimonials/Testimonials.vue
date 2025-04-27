<template>
  <div class="testimonial-blog">
    <div class="grid-container">
      <!-- Image Slider -->
      <Splide
        :options="settingsImg"
        ref="sliderImage"
        @move="handleSyncImage"
        class="image-slide"
      >
        <SplideSlide v-for="(item, index) in testiContent" :key="index">
          <div class="image-wrapper">
            <img :src="item.img" alt="testimonial" />
          </div>
        </SplideSlide>
      </Splide>

      <!-- Testimonial Text Slider -->
      <div class="testimonial-text">
        <Splide
          :options="settingsText"
          ref="sliderText"
          @move="handleSyncText"
          class="text-slide"
        >
          <SplideSlide v-for="(item, index) in testiContent" :key="index">
            <div class="text-wrapper">
              <h4>Testimonials</h4>
              <p class="description">{{ item.text }}</p>
              <div class="author">
                <p class="name">{{ item.name }}</p>
                <p class="title">{{ item.title }}</p>
              </div>
            </div>
          </SplideSlide>
        </Splide>

        <!-- Buttons -->
        <div class="nav-buttons">
          <button @click="slickPrev" class="prev-btn">←</button>
          <button @click="slickNext" class="next-btn">→</button>
        </div>
      </div>

      
      <!-- blog Text Slider -->
      <div class="blog-section ">
        <Splide
          :options="settingsText"
          ref="sliderText"
          @move="handleSyncText"
          class="text-slide"
        >
          <SplideSlide v-for="(item, index) in blogContent" :key="index">
            <div class="text-wrapper">
              <h4>From Our blog</h4>
              <p class="description">{{ item.text }}</p>
              <div class="author">
    
              </div>
            </div>
            
          </SplideSlide>
        </Splide>
        <div class="blog-image">
        
      
    </div>
        <!-- Buttons -->
        <div class="nav-buttons">
          <button @click="slickPrev" class="prev-btn">←</button>
          <button @click="slickNext" class="next-btn">→</button>
        </div>
      </div>
    <Splide
        :options="settingsImg"
        ref="sliderImage"
        @move="handleSyncImage"
        class="image-slide"
      >
      <SplideSlide v-for="(item, index) in blogContent" :key="index">
          <div class="image-wrapper">
            <img :src="item.img" alt="testimonial" />
          </div>
        </SplideSlide>
      </Splide>
    
      </div>
    
  </div>
</template>

<style lang="scss" scoped>
@import './testi-style.scss';
</style>

<script>
import { Splide, SplideSlide } from '@splidejs/vue-splide';


const testiContent = [
  {
    text:
      "Every time I wear it, I get endless compliments — it’s like carrying a little bit of Parisian romance wherever I go. I love how it’s both soft and vibrant, leaving a lasting impression without ever feeling overpowering. Truly, a fragrance that makes you feel beautiful inside and out.",
    img:"/products/miss.png" ,
    name:'Mimo Reed',
    title:'customer',
    
  },
  {
    text:
      'My husban loved this set ',
    img:"/products/collection.png" ,
   
    name:'Emmy gella',
    title:'customer',
  },
  {
    text:
      'Such a comfy Girly dress,Loove it!!',
    img: "/products/ribbon1.jpg",
    name:'Serah teshna',
    title:'customer',
  },
  {
    text: 'Sed imperdiet enim ligula, vitae viverra justo porta vel.',
    img: "/products/ribbon2.jpg",
   name:'Miguel neem',
   title:'customer',
  },
];

const blogContent= [
  {
    text:" What you need to Login to your Findme Account",
    img:"/products/Find5.jpg" ,
  
  },
  {
    text:
      'Look at available clothes ',
    img:"/products/Find3.jpg" ,
   
  },
  {
    text:
      'Enter the product code and search if its present',
    img:"/products/Find6.jpg" ,
  
  },
  {
    text:
      'Enter these details to register a new account with find me',
    img:"/products/Find1.jpg" ,
  
  },
];
export default {
  components: {
    Splide,
    SplideSlide,
  },
  data() {
    return {
      testiContent,
      blogContent,
      settingsImg: {
        pagination: false,
        type: 'fade',
        speed: 500,
        autoplay: true,
        interval: 10000,
        arrows: false,
        direction: 'ltr',
        reducedMotion: {
          speed: 500,
          rewindSpeed: 1000,
        },
      },
      settingsText: {
        pagination: false,
        type: 'loop',
        speed: 500,
        autoplay: true,
        interval: 10000,
        arrows: false,
        updateOnMove: true,
        direction: 'ltr',
        reducedMotion: {
          speed: 500,
          rewindSpeed: 1000,
        },
      },
    };
  },
  mounted() {
    setTimeout(() => {
      if (this.$vuetify.locale.isRtl) {
        this.settingsImg.direction = 'rtl';
        this.settingsText.direction = 'rtl';
      } else {
        this.settingsImg.direction = 'ltr';
        this.settingsText.direction = 'ltr';
      }
    }, 100);
  },
  methods: {
    slickNext() {
      this.$refs.sliderText.go('>');
    },
    slickPrev() {
      this.$refs.sliderText.go('<');
    },
    handleSyncText(slide) {
      this.$refs.sliderImage.go(slide.index);
    },
    handleSyncImage(slide) {
      this.$refs.sliderText.go(slide.index);
    },
    goToSlide(index) {
      this.$refs.sliderText.go(index);
      this.$refs.sliderImage.go(index);
    },
  },
};



</script>