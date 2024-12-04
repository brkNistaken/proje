<template>
  <div>
    <!-- Sayfa içerikleri -->
    <Gallery v-show="pageCount === 1" />
    <TracksuitCollection v-show="pageCount === 2" />
    <Sapka v-show="pageCount === 3" />
    <Filtreleme v-show="pageCount === 4" /> <!-- Filtreleme bileşenini ekliyoruz -->
    <RegisterForm v-show="pageCount === 5" /> <!-- RegisterForm bileşenini ekliyoruz -->

    <!-- Navigasyon düğmeleri -->
    <button id="nextButton" @click="addCounter">Sıradaki Sayfaya Geç</button>
    <button id="preButton" @click="subCounter">Önceki Sayfaya Dön</button>
  </div>
</template>

<script>
import Gallery from "@/components/Gallery.vue"; // Gallery bileşenini içe aktarıyoruz.
import TracksuitCollection from "./components/TracksuitCollection.vue"; // TracksuitCollection bileşeni
import Sapka from "./components/Sapka.vue"; // Sapka bileşeni
import Filtreleme from "./components/Filtreleme.vue"; // Filtreleme bileşenini içe aktarıyoruz
import RegisterForm from "@/components/RegisterForm.vue"; // RegisterForm bileşenini içe aktarıyoruz

export default {
  components: {
    Gallery,
    TracksuitCollection,
    Sapka,
    Filtreleme,
    RegisterForm, // RegisterForm bileşenini burada tanımlıyoruz
  },
  data() {
    return {
      pageCount: 0, // Varsayılan sayfa
    };
  },
  methods: {
    addCounter() {
      if (this.pageCount < 5) { // Sayfa sayısını 5'e kadar arttırıyoruz
        this.pageCount += 1;
      }
    },
    subCounter() {
      if (this.pageCount > 0) {
        this.pageCount -= 1;
      }
    },
  },
};
</script>

<style scoped>
.title {
  text-align: center;
  margin: 20px 0;
  font-size: 24px;
  font-weight: bold;
}
#nextButton {
  color: white;
  background-color: darkblue;
  padding: 10px;
  border-radius: 10px;
  cursor: pointer;
}
#preButton {
  color: white;
  background-color: darkred;
  padding: 10px;
  border-radius: 10px;
  cursor: pointer;
}
</style>
