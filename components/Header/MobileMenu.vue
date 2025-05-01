<template>
  <div class="mobile-nav paper-nav">
    <div
      v-show="open"
      :class="{ 'menu': true, 'menu-open': open }"
    >
      <v-list
        dense
        tag="nav"
        role="navigation"
        aria-label="Mobile navigation menu"
      >
        <v-list-item
          v-for="(item, index) in navMenu"
          :key="item"
          :href="'#' + item"
        >
          <v-list-item-title
            class="menu-list"
            :style="{ animationDelay: (index * 0.15) + 's' }"
          >
            {{ $t('fashionLanding.header_' + item) }}
          </v-list-item-title>
        </v-list-item>
      </v-list>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import './header-style';
</style>

<script>
import navMenu from './menu';
import link from '@/assets/text/link';

export default {
  props: {
    open: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      link,
      navMenu,
    };
  },
};
</script>
