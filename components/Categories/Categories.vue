<template>
  <div class="root">
    <v-container :class="{ 'fixed-width': isDesktop }">
      <v-row class="spacing3">
        <v-col md="6" cols="12">
          <title-main
            :align="isMobile ? 'center' : 'left'"
            primary="Top"
            secondary="Categories"
          />
        </v-col>
        <v-col md="3" sm="6" cols="12"  class="category-image">
          <category-full-card
            img="/products/imagea.jpg"
            title="Woman Shoes"
            
            background="eddacf"
          />
        </v-col>
        <v-col md="3" sm="6" cols="12">
          <category-full-card
            img="/products/imagei.jpg"
            title="Woman bag"
            
            background="e7ddd9"
          />
        </v-col>
      </v-row>
      <v-row class="spacing3">
        <v-col md="6" cols="12" class="py-0">
          <category-half-card
          img="/products/image5.jpg"
            title="Men Casual"
            
            background="D9D8C9"
            type="top-over"
          />
          <v-row class="spacing3">
            <v-col md="6" sm="6" cols="12">
              <category-full-card
                img="/products/imagem.jpg"
                title="Men Watch"
                
                background="e7ddd9"
              />
            </v-col>
            <v-col md="6" sm="6" cols="12">
              <category-full-card
              img="/products/imagen.jpg"
                title="Men Shoes"
                
                background="f2dede"
              />
            </v-col>
          </v-row>
        </v-col>
        <v-col md="6" cols="12" class="py-0">
          <category-half-card
            img="/products/sportsw.jpg"
            title="Woman Sport"
            
            background="f3f7bc"
            type="bottom-over"
          />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './categories-style.scss';
</style>

<script>
import imgAPI from '@/assets/images/imgAPI';
import Title from '../Title';
import CategoryHalfCard from '../Cards/CategoryHalf';
import CategoryFullCard from '../Cards/CategoryFull';

export default {
  components: {
    CategoryFullCard,
    CategoryHalfCard,
    'title-main': Title,
  },
  data() {
    return {
      imgAPI,
    };
  },
  computed: {
    isDesktop() {
      const lgUp = this.$vuetify.display.lgAndUp;
      return lgUp;
    },
    isMobile() {
      const xsDown = this.$vuetify.display.smAndDown;
      return xsDown;
    },
  },
};
</script>
