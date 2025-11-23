<script setup>
// Linkleri dizi olarak tutuyorum, böylece HTML çok karışmıyor
const aboutLinks = [
  'Mağazalar', 'Profil Bilgilerim', 'Siparişlerim', 'Sephora Kart', 
  'Kampanyalar', 'Sephora Blog', 'Sıkça Sorulan Sorular', 'Sitemap', 'Bize Ulaşın'
]

const legalLinks = [
  'Genel Şartlar ve Koşullar', 'Çerez Aydınlatma Metni', 'Müşteri Aydınlatma Metni',
  'Mesafeli Satış Sözleşmesi', 'İade Prosedürü', 'Gizlilik ve Güvenlik',
  'KVK Politikası', 'Çerez Ayarları', 'İletişim', 'Yorumların yayınlanma koşulları'
]

// Yukarı çıkma fonksiyonu
const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
}
</script>

<template>
  <footer class="site-footer">
    <div class="container">
      
      <div class="footer-top">
        
        <div class="footer-col">
          <h3>Hakkımızda</h3>
          <ul>
            <li v-for="link in aboutLinks" :key="link">
              <a href="#">{{ link }}</a>
            </li>
          </ul>
          
          <div class="disclaimer">
            <p>Promosyon koşullarını <a href="#">kampanyalar</a> sayfasında bulabilirsin.</p>
            <p>Parfüm kategorisine özel teklif*</p>
          </div>
        </div>

        <div class="footer-col">
          <h3>Üyelik Sözleşmesi</h3>
          <ul>
            <li v-for="link in legalLinks" :key="link">
              <a href="#">{{ link }}</a>
            </li>
          </ul>
        </div>

        <div class="footer-col right-col">
          
          <div class="social-section">
            <h3>Bizi takip et</h3>
            <div class="social-content">
              <div class="qr-box">
                <span>QR</span>
              </div>
              <div class="social-icons">
                <span class="icon">instagram</span>
                <span class="icon">facebook</span>
                <span class="icon">youtube</span>
              </div>
            </div>
            <p class="etbis">ETBİS'e Kayıtlıdır.</p>
          </div>

          <div class="app-section">
            <h3>Sephora App'i indir</h3>
            <div class="app-buttons">
              <button class="store-btn">Google Play</button>
              <button class="store-btn">App Store</button>
            </div>
          </div>

        </div>
      </div>

      <div class="footer-bottom">
        <div class="country-selector">
          <span class="flag">🇹🇷</span>
          <span>Türkiye</span>
        </div>
        
        <button @click="scrollToTop" class="scroll-top-btn">
          ^
        </button>
      </div>

    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  background-color: #000;
  color: #fff;
  padding: 40px 0 20px;
  font-family: sans-serif;
  font-size: 14px;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Sütun Düzeni */
.footer-top {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  border-bottom: 1px solid #333;
  padding-bottom: 30px;
}

.footer-col {
  flex: 1;
  min-width: 250px;
  margin-bottom: 20px;
}

h3 {
  font-size: 16px;
  margin-bottom: 20px;
  font-weight: 700;
}

/* Link Listeleri */
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 12px;
}

a {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s;
}

a:hover {
  color: #fff;
  text-decoration: underline;
}

/* Küçük Açıklama Yazıları */
.disclaimer {
  margin-top: 30px;
  font-size: 12px;
  color: #999;
  line-height: 1.5;
}

/* Sağ Taraf (QR ve App) */
.right-col {
  display: flex;
  flex-direction: column;
  align-items: flex-end; /* Sağa yaslama */
}

.social-content {
  display: flex;
  gap: 15px;
  align-items: center;
}

.qr-box {
  background: white;
  color: black;
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}

.social-icons .icon {
  display: inline-block;
  margin-left: 10px;
  font-size: 10px;
  border: 1px solid white;
  padding: 5px;
  border-radius: 5px;
}

.etbis {
  font-size: 10px;
  color: #999;
  text-align: right;
  margin-top: 5px;
}

.app-buttons {
  display: flex;
  gap: 10px;
  margin-top: 10px;
}

.store-btn {
  background: black;
  color: white;
  border: 1px solid white;
  padding: 8px 15px;
  border-radius: 5px;
  cursor: pointer;
}

/* Alt Bar (Türkiye ve Buton) */
.footer-bottom {
  display: flex;
  justify-content: flex-end; /* Sağa yaslama */
  align-items: center;
  padding-top: 20px;
  position: relative;
}

.country-selector {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: bold;
}

.flag {
  font-size: 20px;
}

.scroll-top-btn {
  background-color: #000;
  color: white;
  border: 1px solid #333;
  width: 40px;
  height: 40px;
  cursor: pointer;
  font-size: 20px;
  margin-left: 20px;
}
</style>