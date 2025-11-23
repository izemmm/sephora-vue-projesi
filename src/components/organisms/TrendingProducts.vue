<script setup>
import { ref } from 'vue'

import img1 from '@/assets/trend-1.png'
import img2 from '@/assets/trend-2.png'
import img3 from '@/assets/trend-3.png'
import img4 from '@/assets/trend-4.png'
import img5 from '@/assets/trend-5.png'
import img6 from '@/assets/trend-6.png'
import img7 from '@/assets/trend-7.png'
import img8 from '@/assets/trend-8.png'

// Ürün Listesi 
const products = [
  {
    id: 1,
    image: img6,
    brand: 'THE ORDINARY',
    name: 'Hyaluronic Acid 2% + B5 Derinlemesine Nemlendirici...',
    price: '395,00', 
    rating: 4.5,
    reviews: 96,
    variant: '2 formatta mevcuttur',
    badge: null
  },
  {
    id: 2,
    image: img2,
    brand: 'SEPHORA COLLECTION',
    name: 'Size Up Waterproof Maskara',
    price: '899,00',
    rating: 4,
    reviews: 44,
    variant: null,
    badge: '300TL üzeri -%50'
  },
  {
    id: 3,
    image: img8,
    brand: 'SEPHORA COLLECTION',
    name: 'Moisturizing Hydratant Dudak Nemlendiricisi',
    price: '399,00',
    rating: 4.5,
    reviews: 87,
    variant: '4 formatta mevcuttur',
    badge: '2.Ürün -%50'
  },
  {
    id: 4,
    image: img3,
    brand: 'THE ORDINARY',
    name: 'Caffeine Solution 5% + EGCG Koyu Halka ve Şiş Görünüm...',
    price: '390,00',
    rating: 4,
    reviews: 52,
    variant: null,
    badge: null
  },
  {
    id: 5,
    image: img4,
    brand: 'SEPHORA COLLECTION',
    name: 'Advent Takvimi - Makyaj, cilt bakımı, banyo ürünleri ve aksesuarlarda 24 sürpriz',
    price: '3.799',
    rating: 5,
    reviews: 24,
    variant: '2 formatta mevcuttur',
    badge: '2.Ürün -%50'
  },
  
  {
    id: 6,
    image: img5, 
    brand: 'SEPHORA COLLECTİON',
    name: 'Mega Mix Palette',
    price: '1.099,00',
    rating: 5,
    reviews: 1200,
    variant: '12 formatta mevcuttur',
    badge: 'Çok Satan'
  },
  {
    id: 7,
    image: img1, 
    brand: 'SEPHORA COLLECTİON',
    name: 'Outrageous Plump Effect Gloss - Dolgunlaştırıcı Dudak Parlatıcısı',
    price: '899,00',
    rating: 4.8,
    reviews: 850,
    variant: '8 formatta mevcuttur',
    badge: null
  },
  {
    id: 8,
    image: img7, 
    brand: 'SEPHORA COLLECTİON',
    name: 'Size up - Anında XL Etkili Hacim Verici Maskara',
    price: '899,00',
    rating: 4.9,
    reviews: 540,
    variant: '2 formatta mevcuttur',
    badge: 'Yeni'
  }
]

// Scroll İşlemlerim
const scrollContainer = ref(null)

const scrollLeft = () => {
  if (scrollContainer.value) {
    scrollContainer.value.scrollBy({ left: -300, behavior: 'smooth' })
  }
}

const scrollRight = () => {
  if (scrollContainer.value) {
    scrollContainer.value.scrollBy({ left: 300, behavior: 'smooth' })
  }
}
</script>

<template>
  <div class="trending-section">
    
    <div class="section-header">
      <h2>En Trend Ürünler</h2>
      <button class="view-all-btn">Tüm ürünleri görüntüle</button>
    </div>

    <div class="slider-container">
      
      <button class="arrow-btn left" @click="scrollLeft">‹</button>

      <div class="products-track" ref="scrollContainer">
        
        <div v-for="product in products" :key="product.id" class="product-card">
          
          <div v-if="product.badge" class="badge">{{ product.badge }}</div>

          <button class="heart-btn">♡</button>

          <div class="image-wrapper">
            <img :src="product.image" :alt="product.name">
          </div>

          <div class="card-info">
            <h3 class="brand">{{ product.brand }}</h3>
            <p class="name">{{ product.name }}</p>
            
            <div class="price-area">
              <span v-if="product.name.includes('Hyaluronic')" class="start-price">Başlangıç fiyatı</span>
              <span class="price">₺{{ product.price }}</span>
            </div>
            
            <div class="rating">
              <span class="stars">★★★★☆</span>
              <span class="review-count">{{ product.reviews }} Yorum</span>
            </div>

            <p v-if="product.variant" class="variant-info">{{ product.variant }}</p>
            <p v-else class="variant-info" style="visibility: hidden;">-</p>

            <button class="discover-btn">Keşfet</button>
          </div>
        </div>

      </div>

      <button class="arrow-btn right" @click="scrollRight">›</button>

    </div>

  </div>
</template>

<style scoped>
.trending-section {
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  padding: 20px;
  max-width: 1200px;
  margin: 0 auto;
}

/* Başlık */
.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.section-header h2 {
  font-size: 24px;
  font-weight: 800;
}

/*  BUTON STİLİ  */
.view-all-btn {
  background: white;
  border: 1px solid #ddd;
  padding: 8px 15px;
  font-weight: bold;
  border-radius: 4px;
  cursor: pointer;
  font-size: 12px;
  transition: all 0.1s ease; 
}

/* Mouse üstüne gelince */
.view-all-btn:hover {
  border-color: black;
  background-color: #f9f9f9;
}

/* Tıklayınca basma efekti */
.view-all-btn:active {
  transform: scale(0.95); 
  background-color: #e5e5e5;
}


/* Slider Yapısı */
.slider-container {
  position: relative;
  display: flex;
  align-items: center;
}

.products-track {
  display: flex;
  gap: 15px;
  overflow-x: auto; /* Yatay kaydırma */
  scroll-behavior: smooth;
  padding: 10px 0;
  scrollbar-width: none; 
}
.products-track::-webkit-scrollbar {
  display: none;
}

/* Ürün Kartı */
.product-card {
  min-width: 200px; 
  max-width: 200px;
  
  padding: 10px;
  position: relative;
  background: white;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 480px;
}

.badge {
  position: absolute;
  top: 0;
  left: 0;
  background-color: black;
  color: white;
  font-size: 10px;
  font-weight: bold;
  padding: 3px 6px;
  z-index: 2;
}

.heart-btn {
  position: absolute;
  top: 0;
  right: 0;
  background: none;
  border: none;
  font-size: 22px;
  cursor: pointer;
  z-index: 2;
}

.image-wrapper {
  height: 220px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 10px;
}

.image-wrapper img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

/* Kart Bilgileri */
.card-info {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.brand {
  font-size: 12px;
  font-weight: 900;
  margin-bottom: 5px;
  text-transform: uppercase;
}

.name {
  font-size: 13px;
  line-height: 1.4;
  margin-bottom: 15px;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  height: 54px;
}

.price-area {
  margin-bottom: 5px;
}

.start-price {
  font-size: 11px;
  display: block;
  color: #333;
}

.price {
  font-size: 14px;
  font-weight: 900;
}

.rating {
  font-size: 11px;
  margin-bottom: 5px;
  display: flex;
  align-items: center;
  gap: 5px;
}

.variant-info {
  font-size: 11px;
  color: #666;
  margin-bottom: 15px;
}

/* Keşfet Butonu */
.discover-btn {
  width: 100%;
  background: white;
  border: 1px solid black;
  color: black;
  padding: 10px;
  font-weight: 800;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.2s;
  margin-top: auto;
  font-size: 14px;
}

.discover-btn:hover {
  background: #f0f0f0;
}

/* Ok Butonları */
.arrow-btn {
  background-color: black;
  color: white;
  border: none;
  width: 40px;
  height: 40px;
  font-size: 24px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
  position: absolute;
  z-index: 10;
}

.left {
  left: -20px;
}

.right {
  right: -20px;
}
</style>