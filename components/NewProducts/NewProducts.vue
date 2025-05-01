<template>
  <div class="root">
    <v-container :class="{ 'fixed-width': isDesktop }">
      <v-row class="spacing3">
        <v-col md="3" cols="12">
          <title-main
            :align="isMobile ? 'center' : 'left'"
            primary="New"
            secondary="Arrivals"
          />
          <p class="use-text-paragrpah" style="color: white">
            {{ $t('fashionLanding.new_desc') }}
          </p>
        </v-col>
        <v-col md="3" sm="4" cols="12">
          <product-ratting-card
            img="/products/image.jpg"
            :ratting="4"
            text="It is a long established"
          />
        </v-col>
        <v-col md="3" sm="4" cols="12">
          <product-ratting-card
            img="/products/imaged.jpg"
            :ratting="5"
            text="It is a long established"
          />
        </v-col>
        <v-col md="3" sm="4" cols="12">
          <product-ratting-card
            img="/products/imagee.jpg"
            :ratting="5"
            text="It is a long established"
          />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './new-products-style.scss';
</style>

<script>
import imgAPI from '@/assets/images/imgAPI';
import Title from '../Title';
import ProductRattingCard from '../Cards/ProductRatting';

// Modify the ProductRattingCard to remove redirection
export default {
  components: {
    'title-main': Title,
    ProductRattingCard,
  },
  data() {
    return {
      imgAPI,
    };
  },
  computed: {
    isDesktop() {
      const mdUp = this.$vuetify.display.mdAndUp;
      return mdUp;
    },
    isMobile() {
      const xsDown = this.$vuetify.display.smAndDown;
      return xsDown;
    },
  },
};
</script>
