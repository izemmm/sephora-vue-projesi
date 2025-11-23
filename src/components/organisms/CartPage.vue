<script setup>
import { ref } from 'vue'
// Daha önce yüklediğin ana görseli burada da kullanıyoruz
import productImg from '@/assets/ana.png'

const quantity = ref(1)
</script>

<template>
  <div class="checkout-page">
    
    <div class="top-banner">
      Black Friday Sephora Collection ile Başladı!
    </div>

    <header class="simple-header">
      <div class="header-container">
        <div class="logo">SEPHORA</div>
        
        <div class="steps">
          <div class="step active">
            <span class="step-num">1</span>
            <span class="step-text">Adres ve Kargo Bilgileri</span>
          </div>
          <div class="step">
            <span class="step-num inactive">2</span>
          </div>
          <div class="step">
            <span class="step-num inactive">3</span>
          </div>
        </div>
      </div>
    </header>

    <div class="main-content">
      
      <div class="left-col">
        <div class="cart-box">
          <h2>Sepet</h2>
          
          <div class="cart-item">
            <div class="item-img">
              <img :src="productImg" alt="Product">
            </div>

            <div class="item-details">
              <div class="brand-row">
                <h3>YVES SAINT LAURENT</h3>
                <span class="heart-icon">♡</span>
              </div>
              <p class="item-name">MAKE ME BLUSH - Allık</p>
              <p class="item-variant">06 Rose Haze (5 g)</p>

              <div class="actions">
                <select v-model="quantity" class="qty-select">
                  <option>1</option>
                  <option>2</option>
                  <option>3</option>
                </select>
                <button class="remove-btn">KALDIR</button>
              </div>
            </div>

            <div class="item-price">
              2.900 TL
            </div>
          </div>

        </div>
      </div>

      <div class="right-col">
        
        <div class="promo-box">
          <div class="box-header">
            <span>Bir promosyon kodu girin</span>
            <span class="arrow-up">^</span>
          </div>
          <p class="label">Promosyon kodu</p>
          <div class="input-group">
            <input type="text">
            <button class="ok-btn">Ok</button>
          </div>
          <p class="helper-text">Sipariş başına yalnızca bir promosyon kodu kullanabilirsiniz. Kodu harfler arasında boşluk bırakmadan girin.</p>
        </div>

        <div class="summary-box">
          <h3>Sipariş özeti</h3>
          
          <div class="summary-row">
            <span>Ara toplam</span>
            <span>2.900 TL</span>
          </div>
          
          <div class="summary-row">
            <span>Mağazadan Teslimat ⓘ</span>
            <span>Ücretsiz</span>
          </div>

          <div class="progress-section">
            <div class="progress-labels">
              <span>0 TL</span>
              <span>2.000 TL</span>
            </div>
            <div class="progress-bar">
              <div class="progress-fill"></div>
            </div>
            <p class="free-shipping-text">Ücretsiz kargo</p>
          </div>

          <div class="total-row">
            <span>Ürünlerin Toplam Tutarı</span>
            <span>2.900 TL</span>
          </div>
          <p class="tax-info">KDV dahil</p>

          <button class="checkout-btn">Alışverişi tamamla</button>

        </div>

      </div>

    </div>
  </div>
</template>

<style scoped>
/* Genel Sayfa Ayarları */
.checkout-page {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  background-color: #f6f6f6; /* Sayfanın gri arka planı */
  min-height: 100vh;
}

/* 1. Üst Banner */
.top-banner {
  background-color: #feeef3;
  color: #000;
  text-align: center;
  padding: 10px;
  font-size: 13px;
  font-weight: 700;
}

/* 2. Header */
.simple-header {
  background-color: white;
  padding: 20px 0;
  margin-bottom: 30px;
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 28px;
  letter-spacing: 2px;
  font-weight: 600;
}

.steps {
  display: flex;
  align-items: center;
  gap: 15px;
}

.step {
  display: flex;
  align-items: center;
  gap: 10px;
}

.step-num {
  width: 24px;
  height: 24px;
  background-color: #d1245e; /* Kırmızı/Pembe aktif renk */
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  font-weight: bold;
}

.step-num.inactive {
  background-color: #eee;
  color: #999;
}

.step-text {
  font-size: 14px;
  font-weight: 600;
}

/* 3. Ana İçerik */
.main-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  gap: 30px;
}

/* Sol Sütun */
.left-col {
  flex: 2; /* Sol taraf daha geniş */
}

.cart-box {
  background-color: white;
  padding: 30px;
}

.cart-box h2 {
  font-size: 20px;
  margin-bottom: 20px;
}

.cart-item {
  display: flex;
  gap: 20px;
  border-top: 1px solid #eee;
  padding-top: 20px;
}

.item-img img {
  width: 100px;
  height: 100px;
  object-fit: contain;
}

.item-details {
  flex: 1;
}

.brand-row {
  display: flex;
  justify-content: space-between;
  font-weight: 700;
  font-size: 14px;
  margin-bottom: 5px;
}

.heart-icon {
  cursor: pointer;
  font-size: 18px;
}

.item-name { font-size: 14px; margin-bottom: 5px; }
.item-variant { font-size: 13px; color: #666; margin-bottom: 20px; }

.actions {
  display: flex;
  align-items: center;
  gap: 20px;
}

.qty-select {
  padding: 5px 10px;
  border: 1px solid #ddd;
  background: white;
}

/* --- KALDIR BUTONU EFEKTLERİ (YENİ) --- */
.remove-btn {
  background: none;
  border: none;
  font-size: 12px;
  font-weight: bold;
  cursor: pointer;
  text-decoration: underline;
  transition: all 0.1s ease; /* Animasyon */
}

.remove-btn:hover {
  color: #d1245e; /* Üzerine gelince pembe */
  text-decoration: none;
}

.remove-btn:active {
  transform: scale(0.90); /* Tıklayınca küçülme */
  color: #999;
}
/* ------------------------------------- */

.item-price {
  font-weight: 700;
  font-size: 16px;
}

/* Sağ Sütun */
.right-col {
  flex: 1; /* Sağ taraf daha dar */
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* Promo ve Özet Kutuları Ortak Stil */
.promo-box, .summary-box {
  background-color: white;
  padding: 20px;
}

/* Promo Kodu */
.box-header {
  display: flex;
  justify-content: space-between;
  font-weight: 700;
  margin-bottom: 15px;
}

.label { font-size: 12px; margin-bottom: 5px; }

.input-group {
  display: flex;
  gap: 10px;
  margin-bottom: 10px;
}

.input-group input {
  flex: 1;
  border: 1px solid #ddd;
  padding: 8px;
}

.ok-btn {
  background-color: black;
  color: white;
  border: none;
  padding: 0 15px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.1s;
}

.ok-btn:active {
  transform: scale(0.95);
}

.helper-text {
  font-size: 11px;
  color: #666;
  line-height: 1.4;
}

/* Sipariş Özeti */
.summary-box h3 {
  font-size: 18px;
  margin-bottom: 20px;
}

.summary-row {
  display: flex;
  justify-content: space-between;
  font-size: 14px;
  margin-bottom: 15px;
}

.progress-section {
  background-color: #f9f9f9;
  padding: 10px;
  margin-bottom: 20px;
}

.progress-labels {
  display: flex;
  justify-content: space-between;
  font-size: 11px;
  margin-bottom: 5px;
}

.progress-bar {
  height: 6px;
  background-color: #ddd;
  border-radius: 3px;
  margin-bottom: 5px;
}

.progress-fill {
  width: 100%; /* Full dolu */
  height: 100%;
  background-color: black;
  border-radius: 3px;
}

.free-shipping-text {
  font-size: 11px;
  font-weight: bold;
}

.total-row {
  display: flex;
  justify-content: space-between;
  font-weight: 700;
  font-size: 16px;
  margin-top: 10px;
  padding-top: 10px;
  border-top: 1px solid #eee;
}

.tax-info {
  font-size: 11px;
  color: #999;
  margin-bottom: 20px;
}

/* ALIŞVERİŞİ TAMAMLA BUTONU EFEKTLERİ (YENİ) */
.checkout-btn {
  width: 100%;
  background-color: black;
  color: white;
  padding: 15px;
  border: none;
  font-weight: bold;
  cursor: pointer;
  font-size: 14px;
  transition: transform 0.1s ease;
}

.checkout-btn:hover {
  opacity: 0.8;
}

.checkout-btn:active {
  transform: scale(0.98); /* Hafif küçülme */
}
</style>