<template>
  <div class="simple-thumb">
    <v-btn
      variant="plain"
      class="thumb-wrap"
    >
      <span class="wrap">
        <span class="figure">
          <img :src="img" alt="title">
        </span>
        <span class="text">{{ title }}</span>
        <span class="price">
          <strong>{{ price }}</strong>
        </span>
      </span>
    </v-btn>
   
  </div>
</template>

<style lang="scss" scoped>
@import './card-style.scss';

.simple-thumb {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
}


</style>

<script>
import link from '@/assets/text/link';

export default {
  props: {
    img: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    price: {
      type: String,
      required: true,
    },
    phone: {
      type: String,
      default: '0743209616', // Default contact number
    },
  },
  data() {
    return {
      link,
    };
  },
  methods: {
    handleCall() {
      window.location.href = `tel:${this.phone}`;
    },
  },
};
</script>
