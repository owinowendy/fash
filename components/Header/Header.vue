<template>
  <div>
    <v-navigation-drawer
      v-if="isMobile"
      v-model="openDrawer"
      fixed
      temporary
      style="background: none"
    >
      <mobile-menu :open="openDrawer" />
    </v-navigation-drawer>

    <v-app-bar
      id="header"
      v-scroll="handleScroll"
      :class="{ fixed: fixed, 'open-drawer': openDrawer }"
      class="header"
      fixed
      app
    >
      <v-container :class="{ 'fixed-width': isDesktop }">
        <div class="header-content">
          <nav
            :class="{ invert: invert }"
            class="nav-menu"
          >
            <v-btn
              v-if="isMobile"
              :class="{ 'is-active': openDrawer }"
              class="hamburger hamburger--spin mobile-menu"
              text
              icon
              @click.stop="handleToggleOpen"
            >
              <span class="hamburger-box">
                <span class="bar hamburger-inner" />
              </span>
            </v-btn>

            <div class="logo">
              <a
                v-if="invert"
                :href="link.fashion.home"
              >
                <img
                  :src="logo"
                  alt="logo"
                >
              </a>
              <span v-if="!invert && loaded">
                <a
                  v-smooth-scroll="{ offset: 100 }"
                  href="#home"
                  class="anchor-link scrollactive-item"
                >
                  <img
                    :src="logo"
                    alt="logo"
                  >
                </a>
              </span>
            </div>

            <div v-if="isDesktop">
              <ul class="scrollactive-nav">
                <li
                  v-for="(item, index) in menuList"
                  :key="index"
                >
                  <v-btn
                    v-if="!invert"
                    :href="item.url"
                    :class="{ active: activeMenu === item.name }"
                    class="menu-link"
                    variant="text"
                    @click="scrollToMyEl(item.name)"
                  >
                    {{ $t('fashionLanding.header_' + item.name) }}
                  </v-btn>
                  
                  <v-btn
                    v-if="invert"
                    :href="'/' + item.url"
                    variant="text"
                  >
                    {{ $t('fashionLanding.header_' + item.name) }}
                  </v-btn>
                </li>
              </ul>
            </div>
          </nav>
        </div>
      </v-container>
    </v-app-bar>
  </div>
</template>

<style lang="scss" scoped>
@import './header-style.scss';
</style>

<script>
import { inject } from 'vue';
import logo from '@/assets/images/findmelogo.jpg';
import link from '@/assets/text/link';
import brand from '@/assets/text/brand';
import navMenu from './menu';
import MobileMenu from './MobileMenu';
import { useRouter } from '#app';

let counter = 0;
function createData(name, url, offset) {
  counter += 1;
  return {
    id: counter,
    name,
    url,
    offset,
  };
}

export default {
  components: {
    MobileMenu,
  },
  props: {
    invert: {
      type: Boolean,
      default: false,
    },
  },
  setup() {
    const smoothScroll = inject('smoothScroll');
    function scrollToMyEl(elemId) {
      const myEl = document.getElementById(elemId);
      const router = useRouter();

      router.push(`#${elemId}`);
      smoothScroll({
        scrollTo: myEl,
        hash: `#${elemId}`,
        offset: 0,
      });
    }

    return {
      scrollToMyEl,
    };
  },
  data() {
    return {
      logo,
      link,
      loaded: false,
      brand,
      sections: {},
      activeMenu: '',
      fixed: false,
      openDrawer: null,
      menuList: [
        createData(navMenu[0], '#' + navMenu[0], 300),
        createData(navMenu[1], '#' + navMenu[1], 300),
        createData(navMenu[2], '#' + navMenu[2], 300),
        createData(navMenu[3], '#' + navMenu[3], 300),
        createData(navMenu[4], '#' + navMenu[4], 300),
        createData(navMenu[5], '' + navMenu[5], 300),
        createData(navMenu[6], '' + navMenu[6], 300),
      ],
    };
  },
  computed: {
    isMobile() {
      return this.$vuetify.display.smAndDown;
    },
    isDesktop() {
      return this.$vuetify.display.mdAndUp;
    },
  },
  mounted() {
    this.loaded = true;
    const id = window.location.hash;
    const content = id.replace('#', '');
    const element = document.getElementById(content);
    if (element) {
      element.scrollIntoView();
    }

    const section = document.querySelectorAll('.scroll-nav-content > *');
    Array.prototype.forEach.call(section, (e) => {
      this.sections[e.id] = e.offsetTop;
    });
  },
  methods: {
    handleScroll() {
      const scrollPosition = document.documentElement.scrollTop || document.body.scrollTop;
      const topPosition = scrollPosition + 50;

      Object.keys(this.sections).forEach((i) => {
        if (this.sections[i] <= topPosition) {
          this.activeMenu = i;
        }
      });

      this.fixed = scrollPosition > 70;
    },
    handleToggleOpen() {
      this.openDrawer = !this.openDrawer;
    },
  },
};
</script>
