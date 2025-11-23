<script setup>
import { ref } from 'vue'


import img1 from '@/assets/modal-1.png'
import img2 from '@/assets/modal-2.png'
import img3 from '@/assets/modal-3.png'

// Öneri Ürünleri Listesi
const products = [
  {
    id: 1,
    image: img1,
    brand: 'SEPHORA COLLECTION',
    name: 'Size up',
    desc: 'Anında XL Etkili Hacim V...',
    rating: 115,
    price: '899 TL',
    badge: '2.Ürün -%50',
    startPrice: false
  },
  {
    id: 2,
    image: img2,
    brand: 'SEPHORA COLLECTION',
    name: 'BEST SKIN EVER',
    desc: 'Doğal bitişli fondöten, 16...',
    rating: 10,
    price: '899 TL',
    badge: '2.Ürün -%50',
    startPrice: false
  },
  {
    id: 3,
    image: img3,
    brand: 'SEPHORA COLLECTION',
    name: 'Suya Dayanıklı Express ...',
    desc: 'Makyajı Çıkarır + Cildi Ya...',
    rating: 21,
    price: '379 TL',
    badge: '2.Ürün -%50',
    startPrice: true 
  }
]
</script>

<template>
  <div class="modal-card">
    
    <div class="modal-header">
      <div class="success-message">
        <span class="check-icon">✓</span>
        <span>ürün sepete eklendi</span>
      </div>
      <button class="close-btn">✕</button>
    </div>

    <div class="action-buttons">
      <button class="btn black-btn">Alışverişe Devam Et</button>
      <button class="btn white-btn">Sepete git</button>
    </div>

    <hr class="separator" />

    <h3 class="recommendation-title">Şunları da beğenebilirsiniz</h3>

    <div class="rec-list">
      
      <div v-for="product in products" :key="product.id" class="rec-card">
        <div class="badge">{{ product.badge }}</div>
        
        <div class="img-wrapper">
          <img :src="product.image" :alt="product.name">
        </div>

        <div class="info">
          <p class="brand">{{ product.brand }}</p>
          <p class="name">{{ product.name }}</p>
          <p class="desc">{{ product.desc }}</p>
          
          <div class="stars">
            ★★★★☆ <span class="count">{{ product.rating }}</span>
          </div>

          <div class="price-area">
            <span v-if="product.startPrice" class="start-label">Başlangıç Fiyatı: </span>
            <span class="price-text">{{ product.price }}</span>
          </div>
        </div>
      </div>

      <button class="next-arrow">›</button>

    </div>

  </div>
</template>

<style scoped>
.modal-card {
  background: white;
  padding: 20px;
  max-width: 800px;
  margin: 0 auto;
  font-family: 'Arial', sans-serif;
  border: 1px solid #eee; 
  box-shadow: 0 5px 20px rgba(0,0,0,0.1);
}

/* Header */
.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.success-message {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 800;
  font-size: 18px;
  margin: 0 auto; 
  transform: translateX(15px); 
}

.check-icon {
  width: 24px;
  height: 24px;
  border: 1px solid #80c043;
  color: #80c043; 
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
}

.close-btn {
  background: none;
  border: none;
  font-size: 20px;
  cursor: pointer;
  font-weight: bold;
  transition: transform 0.1s;
}
.close-btn:active { transform: scale(0.8); }

/* Butonlar */
.action-buttons {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-bottom: 30px;
}

.btn {
  padding: 12px 30px;
  font-weight: 800;
  font-size: 14px;
  border-radius: 4px;
  cursor: pointer;
  width: 220px;
  transition: transform 0.1s ease, opacity 0.2s;
}

.btn:hover { opacity: 0.85; }
.btn:active { transform: scale(0.95); }

.black-btn { background-color: black; color: white; border: 1px solid black; }
.white-btn { background-color: white; color: black; border: 1px solid black; }

.separator { border: 0; border-top: 1px solid #eee; margin-bottom: 20px; }

/* Öneriler */
.recommendation-title {
  text-align: center;
  font-size: 24px;
  font-weight: 800;
  margin-bottom: 20px;
}

.rec-list {
  display: flex;
  gap: 20px;
  position: relative;
  align-items: flex-start; /* Hizalama */
}

/* ürün kartı efektleri */
.rec-card {
  width: 33%;
  position: relative;
  cursor: pointer; /* Tıklanabilir işareti */
  border-radius: 8px;
  padding: 10px; /* Tıklama alanı için biraz iç boşluk */
  transition: transform 0.1s ease, box-shadow 0.2s ease; /* Animasyon */
}

/* Mouse üzerine gelince */
.rec-card:hover {
  box-shadow: 0 4px 12px rgba(0,0,0,0.05); 
}

/* Tıklayınca (Basma Hissi) */
.rec-card:active {
  transform: scale(0.96); 
  background-color: #f9f9f9; 
}


.badge {
  position: absolute;
  top: 10px; /* Padding eklediğimiz için konumu biraz içeri aldım */
  left: 10px;
  background-color: #d1245e; 
  color: white;
  font-size: 11px;
  font-weight: bold;
  padding: 4px 8px;
  z-index: 2;
}

.img-wrapper {
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 10px;
}

.img-wrapper img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.info { text-align: left; }
.brand { font-size: 12px; font-weight: 900; margin-bottom: 5px; }
.name { font-size: 13px; font-weight: 800; margin-bottom: 5px; }
.desc { font-size: 13px; color: #333; margin-bottom: 10px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.stars { font-size: 12px; margin-bottom: 10px; }
.count { color: #666; font-size: 11px; margin-left: 5px; }
.price-area { font-size: 14px; font-weight: 900; }
.start-label { font-weight: 400; font-size: 13px; }

/* sağ ok butonu efektlerim */
.next-arrow {
  position: absolute;
  right: -15px;
  top: 50%;
  transform: translateY(-50%);
  background-color: #333;
  color: white;
  border: none;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  transition: transform 0.1s ease;
}

.next-arrow:hover { background-color: black; }
.next-arrow:active { transform: translateY(-50%) scale(0.90); }
</style>