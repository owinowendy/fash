<template>
  <div class="grid-section">
    <!-- Perfume Image (Top Left) -->
    <div class="grid-item image-container">
      <img src="@/assets/images/dior.png"/>
    </div>

    <!-- Testimonial (Top Right) -->
    <div class="grid-item testimonial">
      <div class="testimonial-content">
        <h2>Testimonials</h2>
        <p>
          Vestibulum sit amet tortor sit amet libero lobortis semper at et odio.
          In eu tellus tellus. Pellentesque ullamcorper aliquet ultrices. Aenean
          facilisis vitae purus facilisis semper. Nam vitae scelerisque lorem,
          quis tempus libero.
        </p>
        <div class="author">
          <p class="name">Jean Doe</p>
          <p class="role">Chief Digital Officer</p>
        </div>
        <div class="arrows">
          <button>&larr;</button>
          <button>&rarr;</button>
        </div>
      </div>
    </div>

   <!-- Blog Section (Bottom Left) -->
<div class="grid-item blog">
  <div class="blog-gallery">
    <h4>Explore Our Boutique App</h4>
    
    <div class="app-carousel">
      <button class="arrow left" @click="prevImage">&#8592;</button>

      <img :src="appImages[currentImageIndex]" :alt="'App Screenshot ' + (currentImageIndex + 1)" class="app-image" />

      <button class="arrow right" @click="nextImage">&#8594;</button>
    </div>

    <p>Swipe through to see how our boutique app works in real life.</p>
  </div>
</div>

    <!-- Shoes Image (Bottom Right) -->
    <div class="grid-item image-container">
<img src="@/assets/images/sherman.png"/>
  </div>
  </div>
</template>


<style lang="scss" scoped>
@import './testi-style.scss';
</style>

<script setup>
const appImages = [
  "/images/app-screenshot1.jpg",
  "/images/app-screenshot2.jpg",
  "/images/app-screenshot3.jpg"
]

const currentImageIndex = ref(0)

function nextImage() {
  currentImageIndex.value = (currentImageIndex.value + 1) % appImages.length
}

function prevImage() {
  currentImageIndex.value =
    (currentImageIndex.value - 1 + appImages.length) % appImages.length
}
</script>
