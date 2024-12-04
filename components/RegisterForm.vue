<template>
  <div class="signup-form">
    <div class="tabs">
      <button :class="{ active: tab === 'login' }" @click="tab = 'login'">Üye Girişi</button>
      <button :class="{ active: tab === 'signup' }" @click="tab = 'signup'">Üye Ol</button>
    </div>
    <div v-if="tab === 'signup'" class="form">
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="firstName">Ad</label>
          <input id="firstName" type="text" v-model="form.firstName" required />
        </div>
        <div class="form-group">
          <label for="lastName">Soyad</label>
          <input id="lastName" type="text" v-model="form.lastName" required />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input id="email" type="email" v-model="form.email" required />
        </div>
        <div class="form-group">
          <label for="password">Şifre</label>
          <div class="password-input">
            <input
              id="password"
              :type="passwordVisible ? 'text' : 'password'"
              v-model="form.password"
              required
            />
            <button type="button" @click="togglePasswordVisibility" class="show-password-btn">
              <i :class="passwordVisible ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
            </button>
          </div>
        </div>
        <div class="form-group">
          <label for="phone">Telefon</label>
          <div class="phone-input">
            <div class="phone-code" @click="toggleCountryDropdown">
              <img :src="selectedCountry.flag" alt="Country flag" class="country-flag" />
              <div v-if="dropdownVisible" class="country-dropdown">
                <div
                  v-for="country in countries"
                  :key="country.code"
                  class="country-option"
                  @click="selectCountry(country)"
                >
                  <img :src="country.flag" alt="Country flag" class="country-flag" />
                </div>
              </div>
            </div>
            <input
              id="phone"
              type="tel"
              v-model="form.phone"
              :placeholder="selectedCountry.code"
              required
            />
          </div>
        </div>
        <label>
          <input type="checkbox" v-model="form.marketingConsent" />
          <span class="normal-text">Kampanyalardan haberdar olmak için
            <span class="underline-text">Ticari Elektronik İleti Onayı</span> metnini okudum, onaylıyorum.</span>
        </label>
        <label>
          <input type="checkbox" v-model="form.agreementConsent" required />
          <span class="underline-text">Üyelik sözleşmesini ve KVKK Aydınlatma Metnini okudum, kabul ediyorum.</span>
        </label>
        <button type="submit" class="submit-btn">Hesap Oluştur</button>

        <!-- Social Signup Buttons -->
        <div class="social-signup">
          <button type="button" class="google-btn">
            <i class="fab fa-google"></i> Google ile Kayıt Ol
          </button>
          <button type="button" class="facebook-btn">
            <i class="fab fa-facebook-f"></i> Facebook ile Kayıt Ol
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'SignupForm',
  setup() {
    const tab = ref('signup');
    const countries = ref([
      { name: 'Türkiye', code: '+90', flag: 'https://flagcdn.com/w320/tr.png' },
      { name: 'Amerika', code: '+1', flag: 'https://flagcdn.com/w320/us.png' },
      { name: 'Almanya', code: '+49', flag: 'https://flagcdn.com/w320/de.png' },
      { name: 'Fransa', code: '+33', flag: 'https://flagcdn.com/w320/fr.png' },
    ]);

    const selectedCountry = ref(countries.value[0]); // Default: Türkiye
    const dropdownVisible = ref(false);
    const passwordVisible = ref(false); // For toggling password visibility

    const form = ref({
      firstName: '',
      lastName: '',
      email: '',
      password: '', // User's password
      phone: '', // User's phone number
      marketingConsent: false,
      agreementConsent: false,
    });

    const toggleCountryDropdown = () => {
      dropdownVisible.value = !dropdownVisible.value;
    };

    const selectCountry = (country: { name: string; code: string; flag: string }) => {
      selectedCountry.value = country;
      dropdownVisible.value = false;
    };

    const togglePasswordVisibility = () => {
      passwordVisible.value = !passwordVisible.value;
    };

    const handleSubmit = () => {
      if (form.value.agreementConsent) {
        console.log('Form submitted', form.value);
      } else {
        alert('Üyelik sözleşmesini kabul etmelisiniz.');
      }
    };

    return {
      tab,
      countries,
      selectedCountry,
      form,
      passwordVisible,
      handleSubmit,
      toggleCountryDropdown,
      selectCountry,
      togglePasswordVisibility,
      dropdownVisible,
    };
  },
});
</script>

<style scoped>
.signup-form {
  max-width: 400px;
  margin: 0 auto;
  font-family: Arial, sans-serif;
}

.tabs {
  display: flex;
  justify-content: space-between;
  margin-bottom: 16px;
}

.tabs button {
  flex: 1;
  padding: 10px;
  border: none;
  background: #f0f0f0;
  cursor: pointer;
  font-weight: bold;
  text-align: center;
}

.tabs button.active {
  background: black;
  color: white;
}

.form-group {
  margin-bottom: 24px;
  position: relative;
}

.form-group label {
  display: block;
  font-size: 14px;
  font-weight: bold;
  color: #555;
  margin-bottom: 4px;
  text-align: left;
}

input {
  width: 100%;
  padding: 8px 8px 8px 56px;
  border: none;
  border-bottom: 2px solid #ccc;
  outline: none;
  transition: border-color 0.3s ease;
  font-size: 14px;
}

input:focus {
  border-bottom: 2px solid black;
}

.password-input {
  position: relative;
}

.password-input input {
  width: 100%;
  padding-right: 80px; /* Space for the button */
}

.show-password-btn {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  background: transparent;
  border: none;
  color: #007bff;
  cursor: pointer;
  font-size: 18px;
}

.phone-input {
  position: relative;
  display: flex;
  align-items: center;
}

.phone-input .phone-code {
  position: absolute;
  left: 10px;
  display: flex;
  align-items: center;
  cursor: pointer;
  z-index: 1;
}

.phone-input .country-flag {
  width: 24px;
  height: 16px;
}

.phone-input input {
  padding-left: 48px; /* Adjusted to leave space for the flag */
}

.country-dropdown {
  position: absolute;
  top: 30px;
  left: 0;
  background: white;
  border: 1px solid #ccc;
  width: 100%;
  z-index: 2;
}

.country-option {
  padding: 10px;
  cursor: pointer;
}

.country-option:hover {
  background-color: #f0f0f0;
}

.submit-btn {
  width: 100%;
  padding: 10px;
  background: black;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  margin-top: 16px;
}

/* Social signup buttons */
.social-signup {
  margin-top: 20px;
}

.social-signup button {
  width: 100%;
  padding: 12px;
  background: white;
  color: #555;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  margin-bottom: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.social-signup button i {
  margin-right: 8px;
}

.google-btn i {
  color: #db4437;
}

.facebook-btn i {
  color: #3b5998;
}

.google-btn:hover, .facebook-btn:hover {
  background-color: #f0f0f0;
}

/* Altı çizili metinler */
.underline-text {
  text-decoration: underline;
  text-decoration-color: black;
}

.normal-text {
  color: inherit;
}
</style>
