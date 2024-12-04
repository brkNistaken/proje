<template>
  <div class="product-slider">
    <h2 class="title">Çok Satanlar</h2>
    <div class="slider-container">
      <button class="slider-button left" @click="prevSlide">
        &#8249;
       
      </button>
      <div class="products">
        <div
          class="product-card"
          v-for="product in visibleProducts"
          @mouseover="setHoverImage(product)"
          @mouseout="resetImage(product)"
          :key="product.id"
        >
          <img
            :src="getCurrentImage(product)"
            :alt="product.name"
            class="product-image"
          />

          <h3 class="product-name">{{ product.name }}</h3>
          <font-awesome-icon
            style="color: rgb(247, 198, 3)"
            :icon="['fas', 'star']"
          />
          <font-awesome-icon
            style="color: rgb(247, 198, 3)"
            :icon="['fas', 'star']"
          />
          <font-awesome-icon
            style="color: rgb(247, 198, 3)"
            :icon="['fas', 'star']"
          />
          <font-awesome-icon
            style="color: rgb(247, 198, 3)"
            :icon="['fas', 'star']"
          />
          <font-awesome-icon
            style="color: rgb(247, 198, 3)"
            :icon="['fas', 'star-half-stroke']"
          />
          <span style="font-size: 0.75rem">2 değerlendirme</span><br />
          <p class="discount-rate">
            <span v-if="product.discountRate">%{{ product.discountRate }}</span>
          </p>
          <p class="product-price">
            <span class="old-price" v-if="product.oldPrice">
              {{ formatPrice(product.oldPrice) }}
            </span>
            <span class="new-price">
              {{ formatPrice(product.newPrice) }}
            </span>
          </p>
        </div>
      </div>
      <button class="slider-button right" @click="nextSlide">
        &#8250;
       
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ProductSlider",
  data() {
    return {
      products: [
        {
          id: 1,
          name: "Sohigh Boxy Fit E.D.R.S V3 Zip Hoodie",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/6cac7362-27e0-4841-a3a7-6292915c0e0a/1080/y29.webp", 
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/252f3a6f-3f88-42e0-982a-9253b6ef0361/1080/y28.webp",
            oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
        {
          id: 2,
          name: "Sohigh Boxy Fit E.D.R.S V3 Zip Hoodie",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/884a5ac7-b3e3-48ea-9938-8d9a54118868/1080/y24.webp", 
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/0173178b-430e-486e-980d-cbf763cc7bea/1080/y25.webp",
            oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
        {
          id: 3,
          name: "Sohigh Boxy Fit Crew Logo Zip Hoodie",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/8d239f0e-8351-4da6-a920-563772441d6b/1080/y23.webp", 
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/6e02fc92-05ad-47c0-9f47-016b36bd2e51/1080/y22.webp",
            oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
        {
          id: 4,
          name: "Sohigh Boxy Fit Essential Zip Hoodie",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/8d239f0e-8351-4da6-a920-563772441d6b/1080/y23.webp", // Replace with actual image URL
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/6e02fc92-05ad-47c0-9f47-016b36bd2e51/1080/y22.webp",
            oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
        {
          id: 5,
          name: "Sohigh Boxy Fit E.D.R.S V3 Zip Hoodie",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/a07a7e1a-45a8-458d-aef7-c375333fa1a2/1080/y20.webp", // Replace with actual image URL
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/092f1835-1eb5-47cd-a906-4dfe4fca4ab4/1080/y21.webp",
            oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
        {
          id: 6,
          name: "Sohigh Boxy Fit E.D.R.S V3 Zip Hoodie",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/c6f14479-355e-40ec-8ad2-a4a748782f27/1080/y18.webp", // Replace with actual image URL
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/95b8b264-953e-440a-bb31-f9f84a50b853/1080/y19.webp",
            oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
        {
          id: 7,
          name: "Sohigh Boxy Fit Crew Logo Zip Hoodie",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/884a5ac7-b3e3-48ea-9938-8d9a54118868/1080/y24.webp", // Replace with actual image URL
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/0173178b-430e-486e-980d-cbf763cc7bea/1080/y25.webp",
            oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
        {
          id: 8,
          name: "Sohigh Boxy Fit Crew Logo Zip Hoodie ",
          image:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/55330673-00bd-4a1d-92ac-baec6867673e/1080/y17.webp", // Replace with actual image URL
          hoverImage:
            "https://cdn.myikas.com/images/45cf1d92-19fb-4955-871e-36793acf1331/a411601c-acc3-4bd2-92fb-94e84ffd5bc4/1080/y16.webp",
          oldPrice: 1499.00,
          newPrice: 899.00,
          discountRate: 20,
        },
      ],
      currentImages: new Map<number, string | null>(),
      currentSlide: 0, 
      itemsPerPage: 4, 
      autoSlideInterval: null as number | null,
    };
  },
  computed: {
    visibleProducts() {
     
      const start = this.currentSlide * this.itemsPerPage;
      const end = start + this.itemsPerPage;
      return this.products.slice(start, end);
    },
    maxSlide() {
     
      return Math.ceil(this.products.length / this.itemsPerPage) - 1;
    },
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % (this.maxSlide + 1);
    },
    prevSlide() {
      this.currentSlide =
        (this.currentSlide - 1 + (this.maxSlide + 1)) % (this.maxSlide + 1);
      this.resetAutoSlide();
    },
    setHoverImage(product) {
      this.currentImages.set(product.id, product.hoverImage);
      this.resetAutoSlide();
    },
    resetImage(product) {
      this.currentImages.set(product.id, null);
    },
    getCurrentImage(product) {
      return this.currentImages.get(product.id) || product.image;
    },
    formatPrice(price: number): string {
      return `₺ ${price.toFixed(2)}`;
    },
    startAutoSlide() {
      this.autoSlideInterval = window.setInterval(() => {
        this.nextSlide();
      }, 3000); // 3 saniyede bir otomatik kaydırma
    },
    stopAutoSlide() {
      if (this.autoSlideInterval) {
        clearInterval(this.autoSlideInterval);
        this.autoSlideInterval = null;
      }
    },
    resetAutoSlide() {
      this.stopAutoSlide();
      this.startAutoSlide();
    },
  },
  mounted() {
 
    this.startAutoSlide();
  },
  beforeUnmount() {
    
    this.stopAutoSlide();
  },
});
</script>

<style scoped>
.product-slider {
  padding: 20px;
  text-align: center;
}
.title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
  font-family: "Oswald", -apple-system, system-ui, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif !important;
}
.slider-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  position: relative;
}
.products {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  width: 80%;
}
.slider-container .products{
    display: flex;
  transition: transform 0.5s ease-in-out;
}
.product-card {
  overflow: hidden;
  text-align: left;
  cursor: pointer;
}
.product-image {
  width: 100%;
  height: auto;
  object-fit: cover;
}
.product-name {
  font-size: 16px;
  font-weight: bold;
  margin: 10px 0;
}
.product-price {
  margin: 5px 0;
  display: inline-block;
}
.old-price {
  text-decoration: line-through;
  color: #888;
}
.new-price {
  font-weight: bold;
  color: #000;
  display: block;
}
.discount-rate {
  display: inline-block;
  color: white;
  background-color: #000;
  font-weight: bold;
  padding: 5px;
  text-align: center;
  line-height: 30px;
  border-radius: 0%;
}
.slider-button {
  font-size: 24px;
  background: none;
  border: 1px solid black;
  width: 40px; 
  height: 40px;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  padding: 10px;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
  display: flex;
  position: absolute;
  font-weight: bold;
}
.slider-button.left {
  left: 10%;
}

.slider-button.right {
  right: 10%;
}

.slider-container:hover .slider-button {
  opacity: 1;
  visibility: visible;
}
</style>