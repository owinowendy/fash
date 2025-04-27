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

      <!-- Blog Description -->
      <div class="blog-description">
        <h4>From Our Blog</h4>
        <h3>Proin lacinia erat ac</h3>
        <p>
          Vivamus sit amet interdum elit. Proin lacinia erat ac velit tempus auctor.
          Interdum et malesuada fames ac ante ipsum primis in faucibus.
          Aliquam nec ex aliquet, aliquam neque non.
        </p>

        <!-- Buttons -->
        <div class="nav-buttons">
          <button class="prev-btn">←</button>
          <button class="next-btn">→</button>
        </div>
      </div>

      <!-- Blog Image -->
      <div class="blog-image">
        <img src="/fashion-theme/assets/images/Login.jpg" alt="Blog" />
      </div>
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
    name: 'Emily l',
    title: 'Marketing Executive',
  },
  {
    text:
      'Vestibulum sit amet tortor sit amet libero lobortis semper at et odio. In eu tellus tellus. Pellentesque ullamcorper aliquet ultrices. Aenean facilisis vitae purus facilisis semper. Nam vitae scelerisque lorem, quis tempus libero.',
    img:"/products/collection.png" ,
    name: 'Jean Doe',
    title: 'Chief Digital Officer',
  },
  {
    text:
      'Cras convallis lacus orci, tristique tincidunt magna consequat in. In vel pulvinar est, at euismod libero.',
    img: "/products/ribbon1.jpg",
    name: 'Jena Doe',
    title: 'Graphic Designer',
  },
  {
    text: 'Sed imperdiet enim ligula, vitae viverra justo porta vel.',
    img: "/products/ribbon2.jpg",
    name: 'Jovelin Doe',
    title: 'Senior Graphic Designer',
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
  },
};
</script>

<style lang="scss" scoped>
.testimonial-blog {
  padding: 2rem;
  background: #f5f5f5;

  .grid-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 300px);
    gap: 0;

    .image-slide,
    .testimonial-text,
    .blog-description,
    .blog-image {
      position: relative;
      overflow: hidden;
    }

    .image-wrapper img,
    .blog-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .testimonial-text {
      background: #2f3e46;
      color: white;
      padding: 2rem;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-start;

      h4 {
        font-size: 1.5rem;
        margin-bottom: 1rem;
      }

      .description {
        margin-bottom: 2rem;
        font-size: 1rem;
      }

      .author {
        .name {
          font-weight: bold;
          font-size: 1.2rem;
        }

        .title {
          font-size: 0.9rem;
          opacity: 0.7;
        }
      }

      .nav-buttons {
        margin-top: 1.5rem;

        button {
          background: #1c262b;
          border: none;
          color: white;
          padding: 0.5rem 1rem;
          margin-right: 0.5rem;
          cursor: pointer;
          border-radius: 5px;
          font-size: 1.2rem;

          &:hover {
            background: #000;
          }
        }
      }
    }

    .blog-description {
      background: #9a8c98;
      color: white;
      padding: 2rem;
      display: flex;
      flex-direction: column;
      justify-content: center;

      h4 {
        font-size: 1.3rem;
        margin-bottom: 0.5rem;
      }

      h3 {
        font-size: 1.8rem;
        margin-bottom: 1rem;
      }

      p {
        font-size: 1rem;
        opacity: 0.9;
      }

      .nav-buttons {
        margin-top: 1.5rem;

        button {
          background: #7c6e7f;
          border: none;
          color: white;
          padding: 0.5rem 1rem;
          margin-right: 0.5rem;
          cursor: pointer;
          border-radius: 5px;
          font-size: 1.2rem;

          &:hover {
            background: #000;
          }
        }
      }
    }
  }
}
</style>
