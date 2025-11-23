<script setup>
const links = [
  'Sephora Collection', 'En Yeniler', 'Özel Setler', 'Trendler',
  'Makyaj', 'Parfüm', 'Cilt Bakımı', 'Vücut ve Banyo', 'Saç',
  'Minis & More', 'Markalar', 'Kampanyalar'
]
</script>

<template>
  <nav class="main-nav">
    <ul>
      <li v-for="link in links" :key="link">
        <a href="#" :class="{ 'pink-text': link === 'Sephora Collection' }">
          {{ link }}
        </a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.main-nav {
  border-top: 1px solid #eee;
  padding: 18px 0; /* Yüksekliği biraz artırdım, ferah olsun */
  background-color: white;
}

ul {
  display: flex;
  justify-content: center; /* Tam ortalar */
  align-items: center;
  list-style: none;
  gap: 35px; /* BOŞLUK ARTIRILDI: Yazılar birbirine yapışmaz */
  margin: 0;
  padding: 0;
  flex-wrap: wrap; /* Ekran küçülürse taşmasın */
}

li {
  display: flex;
  align-items: center;
}

a {
  text-decoration: none;
  color: #000;
  font-weight: 750; /* Kalınlık (Görseldeki gibi bold) */
  font-size: 12px; /* BOYUT KÜÇÜLTÜLDÜ: Daha zarif durur */
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  letter-spacing: 0.5px; /* Harfler arası çok hafif boşluk */
  
  /* --- BASMA EFEKTİ AYARLARI --- */
  display: inline-block;
  transition: transform 0.1s ease, color 0.2s;
}

/* Sadece ilk yazı (Sephora Collection) pembe */
.pink-text {
  color: #d1245e !important;
}

/* --- EFEKTLER --- */

/* Mouse üzerine gelince */
a:hover {
  color: #555;
}

.pink-text:hover {
  color: #a01540 !important;
}

/* Tıklayınca (Basma Hissi) */
a:active {
  transform: scale(0.92); /* Hafifçe küçülür */
  color: #999;
}
</style>