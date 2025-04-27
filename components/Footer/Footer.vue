<template>
  <footer class="root">
    <v-container class="max-lg">
      <div class="logo">
        <img :src="logo" alt="logo">
      </div>
      <div class="subscribe">
        <h5 class="use-text-subtitle">
          Account Deletion

        </h5>
        <div class="form">
          <form>
            <v-text-field
              :placeholder="$t('fashionLanding.subscribe_email')"
              class="field"
              full-width
            />
            <v-btn variant="outlined" class="button" @click="refreshPage"> Submit
             </v-btn>
          </form>
        </div>
      </div>
      <nav>
        <ul>
          <li
            v-for="(item, index) in menu"
            :key="index"
          >
            <a :href="'#' + item">
              {{ $t('fashionLanding.header_' + item) }}
            </a>
          </li>
        </ul>
      </nav>
      <div class="socmed">
        <v-btn variant="flat" icon class="icon">
          <i class="ion-logo-twitter " />
        </v-btn>
        <v-btn variant="flat" icon class="icon">
          <i class="ion-logo-facebook" />
        </v-btn>
        <v-btn variant="flat" icon class="icon">
          <i class="ion-logo-instagram" />
        </v-btn>
      </div>
    </v-container>
    <div class="copyright">
      <p class="body-2 text-center">
        &copy;
        {{ brand.fashion.footerText }}
      </p>
    </div>
  </footer>
</template>

<style scoped lang="scss">
@import './footer-style';
</style>

<script>
import logo from '@/assets/images/findmelogo.jpg';
import brand from '@/assets/text/brand';
import menu from '../Header/menu';

export default {
  data: () => ({
    logo,
    brand,
    menu,
  }),
  mounted() {
    this.updateCopyrightText();
  },
  methods: {
    updateCopyrightText() {
      this.brand.fashion.footerText = 'Findme 2025';
    }
  },
  async deleteAccount() {
      try {
        // Replace this URL with your real endpoint
        await fetch('/api/delete-account', {
          method: 'DELETE'
        });
        
        // Optional: Show a success message, then refresh
        location.reload();
      } catch (error) {
        console.error('Error deleting account:', error);
        // Optionally show error feedback
      }
    }

};

</script>
