<script setup>
import { ref } from 'vue'

// Hangi seçeneğin seçildiğini tutan değişken 
const loyaltyStatus = ref(null) 
</script>

<template>
  <div class="register-card">
    
    <h2>Üye ol</h2>

    <div class="email-info">
      <span class="email-text">izemt1995@icloud.com</span>
      <span class="separator">›</span>
      <a href="#" class="edit-link">Düzenle</a>
    </div>

    <h3 class="question-title">Sephora Sadakat Programı üyesi misin?</h3>
    <p class="description">
      Kolayca Sephora Sadakat Programı üyesi olup tüm ayrıcalıklardan yararlanabilirsin.
    </p>

    <div class="radio-group">
      <label class="radio-label">
        <input type="radio" name="loyalty" value="yes" v-model="loyaltyStatus">
        <span class="radio-text">Evet</span>
      </label>
      
      <label class="radio-label">
        <input type="radio" name="loyalty" value="no" v-model="loyaltyStatus">
        <span class="radio-text">Hayır</span>
      </label>
    </div>

    <p class="info-text">
      Kişisel verileriniz, KVK Politikası ve mevzuatına uygun olarak Sephora tarafından yurtdışına aktarılabilir.
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
.register-card {
  background-color: white;
  padding: 40px;
  max-width: 600px;
  margin: 0 auto;
  font-family: 'Arial', sans-serif;
  color: #000;
}

h2 {
  font-size: 28px;
  font-weight: 800;
  margin-bottom: 20px;
}

/* E-posta Satırı */
.email-info {
  font-size: 14px;
  color: #666;
  margin-bottom: 30px;
  display: flex;
  align-items: center;
  gap: 5px;
}

.email-text {
  color: #333;
}

.separator {
  font-size: 16px;
  color: #999;
}

.edit-link {
  color: #666;
  text-decoration: underline;
  cursor: pointer;
}

/* Soru Alanı */
.question-title {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 10px;
}

.description {
  font-size: 14px;
  margin-bottom: 20px;
  color: #333;
}

/* Radio Butonlarım */
.radio-group {
  display: flex;
  gap: 30px;
  margin-bottom: 30px;
}

.radio-label {
  display: flex;
  align-items: center;
  cursor: pointer;
  font-size: 16px;
}

.radio-label input {
  width: 20px;
  height: 20px;
  margin-right: 10px;
  accent-color: black; /* Seçilince siyah olsun */
  cursor: pointer;
}

ü
.info-text {
  font-size: 13px;
  color: #999; 
  line-height: 1.5;
  margin-bottom: 15px;
}

.required-note {
  font-size: 12px;
  color: #999;
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
  color: #666;
  display: block;
  margin-bottom: 10px;
}

.details-link {
  color: #666;
  font-size: 13px;
  text-decoration: underline;
}
</style>