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
          <p class="use-text-paragrpah">
            {{ $t('fashionLanding.new_desc') }}
          </p>
        </v-col>
        <v-col md="3" sm="4" cols="12">
          <product-ratting-card
            :img="imgAPI.fashion[5]"
            :ratting="4"
            text="It is a long established"
            price="ksh 9000.00"
          />
        </v-col>
        <v-col md="3" sm="4" cols="12">
          <product-ratting-card
            :img="imgAPI.fashion[6]"
            :ratting="5"
            text="It is a long established"
            price="ksh 9000.00"
          />
        </v-col>
        <v-col md="3" sm="4" cols="12">
          <product-ratting-card
            :img="imgAPI.fashion[7]"
            :ratting="5"
            text="It is a long established"
            price="ksh 8000.00"
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
