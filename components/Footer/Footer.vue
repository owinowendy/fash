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
            v-model="email"  
              :placeholder="$t('fashionLanding.subscribe_email')"
              class="field"
              full-width
            />
            <v-btn variant="outlined" class="button" @click="deleteAccount"> Submit
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
            <a :href="item=='privacy_policy'? item :'#' + item">
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
    if (!this.email) {
    alert('Email is required to delete account.');
    return;
  }
  if (!confirm(`Are you sure you want to delete the account for ${this.email}?`)) {
    return;
  }
      try {
        // Replace this URL with your real endpoint
        await fetch('https://us-central1-findme-eed39.cloudfunctions.net/deleteAccount', {
          method: 'DELETE',
          headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        email: this.email
      })
        });
        if (!response.ok) {
      throw new Error('Failed to delete account');
    }

    const data = await response.json();
    console.log('Account deleted:', data);

    // Clear the email field
    this.email = '';

    // Optional: Show success message
    alert('Account deleted successfully');

        
        // Optional: Show a success message, then refresh
        location.reload();
      } catch (error) {
        console.error('Error deleting account:', error);
        // Optionally show error feedback
      }
    }

};

</script>

