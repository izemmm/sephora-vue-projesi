<script setup>
import { ref } from 'vue'

const email = ref('')
const hasError = ref(false)

// Butona basılınca çalışacak fonksiyonum
const handleSubmit = () => {
  // Eğer email boşsa hata veriyo
  if (!email.value || email.value.trim() === '') {
    hasError.value = true
  } else {
    hasError.value = false
    alert(`Giriş yapılıyor: ${email.value}`) 
  }
}
</script>

<template>
  <div class="login-card">
    
    <h2>Giriş yap / Üye ol</h2>
    <p class="sub-title">Giriş yapmak ya da üye olmak için email adresini gir</p>

    <div class="input-wrapper">
      <input 
        type="email" 
        v-model="email" 
        placeholder="Email*" 
        :class="{ 'input-error': hasError }"
      />
      <button @click="handleSubmit" class="ok-btn">OK</button>
    </div>

    <p v-if="hasError" class="error-message">
      Devam etmek için lütfen email adresinizi girin.
    </p>

    <p class="info-text small">
      Kişisel verilerin, KVK Politikası ve mevzuatına uygun olarak Sephora tarafından yurtdışına aktarılabilir.
    </p>
    <p class="required-note">*Zorunlu alan</p>

    <p class="info-text">
      Sephora'nın avantajlarla dolu dünyasına katılarak, güzellik ipuçları, sürprizler ve sana özel fırsatlardan yararlanabilirsin. Sephora hesabın üzerinden siparişlerini takip edebilir, kişisel verilerini ve iletişim tercihlerini güncelleyebilir, teslimat ve ödeme bilgilerini kaydederek kolaylıkla siparişini oluşturabilirsin.
    </p>

    <div class="legal-link">
      <strong>Kişisel verilerin kullanımı:</strong>
      <p class="info-text">Bu formda sağlanan kişisel veriler Sephora Kozmetik A.Ş. tarafından işlenecektir.</p>
      <a href="#" class="details-link">Verilerinin kullanımıve haklarınız ve hakların hakkında daha fazla bilgiye buradan ulaşabilirsin. ⌄</a>
    </div>

  </div>
</template>

<style scoped>
.login-card {
  background-color: white;
  padding: 40px;
  max-width: 600px;
  margin: 0 auto; /* Ortalamak için */
  font-family: 'Arial', sans-serif;
  color: #000;
}

h2 {
  font-size: 24px;
  font-weight: 800;
  margin-bottom: 20px;
}

.sub-title {
  font-size: 16px;
  margin-bottom: 20px;
}

/* Input ve Buton Yan Yana olsun diye */
.input-wrapper {
  display: flex;
  height: 50px;
  margin-bottom: 5px;
}

input {
  flex: 1; /* Kalan tüm alanı kaplasın diye */
  padding: 0 15px;
  font-size: 16px;
  border: 1px solid #ccc;
  outline: none;
}

/* Hata durumunda input kenarı kırmızı olsun diye */
input.input-error {
  border: 1px solid #d1245e;
  color: #d1245e;
}

/* Placeholder rengi */
::placeholder {
  color: #999;
}

.ok-btn {
  background-color: #666; 
  color: white;
  border: none;
  width: 60px;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s;
}

.ok-btn:hover {
  background-color: #333;
}

/* Kırmızı Hata Yazısı */
.error-message {
  color: #d1245e;
  font-size: 14px;
  margin-top: 5px;
  margin-bottom: 20px;
}

/* Metin Stilleri */
.info-text {
  font-size: 13px;
  color: #666;
  line-height: 1.5;
  margin-bottom: 15px;
}

.small {
  font-size: 12px;
}

.required-note {
  font-size: 12px;
  color: #666;
  margin-bottom: 20px;
}

.legal-link {
  margin-top: 30px;
  border-top: 1px solid #eee;
  padding-top: 20px;
}

.legal-link strong {
  text-decoration: underline;
  font-size: 14px;
  display: block;
  margin-bottom: 10px;
}

.details-link {
  color: #666;
  font-size: 13px;
  text-decoration: underline;
}
</style>