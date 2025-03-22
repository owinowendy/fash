<template>
  <div class="main-wrap">
    <!-- Header -->
    <header-main invert />

    <main class="container-wrap">
      <!-- Back Button -->
      <div class="back-button">
        <v-btn icon @click="$router.go(-1)">
          <v-icon>mdi-arrow-left</v-icon>
        </v-btn>
        <span class="page-title">Product Details</span>
      </div>

      <!-- Product Image -->
      <v-row justify="center">
        <v-col sm="10" md="8" cols="12" class="px-4">
          <figure class="figure">
            <img :src="product.image" alt="product">
          </figure>
        </v-col>
      </v-row>

      <!-- Report Button -->
      <div class="report-section">
  <v-btn color="red" class="report-button" rounded large>
    <v-icon left>mdi-alert</v-icon> Report
  </v-btn>
</div>


      <!-- Product Details -->
      <v-row justify="center">
        <v-col sm="10" md="8" cols="12" class="px-4">
          <div class="details-box">
            <p><strong>ShopName:</strong> {{ product.shopName || 'IFTIN G1' }}</p>
            <p><strong>Address:</strong> {{ product.address || 'Eastleigh' }}</p>
            <p><strong>Price:</strong> KSH {{ product.price || '800' }}</p>
            <p><strong>Contact:</strong> {{ product.contact || '0743209616' }}</p>

            <!-- Call Button -->
            <v-btn
              rounded="xl"
              color="green"
              :href="'tel:' + (product.contact || '0743209616')"
              class="call-button"
            >
              <v-icon left>mdi-phone</v-icon> Call
            </v-btn>
          </div>
        </v-col>
      </v-row>
    </main>

    <!-- Footer -->
    <section class="space-top">
      <footer-main />
    </section>
  </div>
</template>

<script>
import Header from '@/components/Header';
import Footer from '@/components/Footer';

export default {
  components: {
    'header-main': Header,
    'footer-main': Footer,
  },
  data() {
    return {
      product: {},
    };
  },
  mounted() {
    this.product = this.$route.params.product || {};
  },
  head() {
    return {
      title: this.product.name ? `${this.product.name} - Product Details` : 'Product Details',
    };
  },
};
</script>

<style lang="scss" scoped>
/* Page Layout */
.container-wrap {
  padding: 20px 15px;
  background-color: #f9f9f9;
}

/* Back Button and Title */
.back-button {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 15px;

  .page-title {
    font-size: 18px;
    font-weight: bold;
  }
}

/* Product Image */
.figure {
  text-align: center;
  img {
    width: 100%;
    border-radius: 10px;
    border: 2px solid #ddd;
  }
}

/* Report Button */
.report-section {
  display: flex;
  justify-content: center;
  margin: 10px 0;
  

  .report-button {
    color: white;
    font-size: 14px;
    text-transform: uppercase;
  }
}

/* Product Details Box */
.details-box {
  background: white;
  padding: 15px;
  border-radius: 10px;
  box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
  text-align: left;

  p {
    font-size: 16px;
    color: #444;
    margin: 5px 0;
  }
}

/* Call Button */
.call-button {
  width: 10%;
  margin-top: 15px;
  font-size: 16px;
  text-transform: uppercase;
}
</style>
