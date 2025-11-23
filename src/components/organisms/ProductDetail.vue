<script setup>
import { ref } from 'vue'


import anaResim from '@/assets/ana.png'
import resim1 from '@/assets/ana1.png'
import resim2 from '@/assets/ana2.png'

// DURUM YÖNETİMİ 
const selectedColorId = ref(2) 
const isColorModalOpen = ref(false)
const isFavorite = ref(false)
const isDescriptionExpanded = ref(false)

// RENK LİSTESİ 
const colors = [
  { id: 1, name: '93 Restless Rosé (6 g)', hex: '#ff9eb5', price: '2.900 TL', inStock: true },
  { id: 2, name: '06 Rose Haze (5 g)', hex: '#edaea0', price: '2.900 TL', inStock: true },
  { id: 3, name: '12 Berry', hex: '#ff7f7f', price: '2.900 TL', inStock: false },
  { id: 4, name: '10 Nude', hex: '#eec7b5', price: '2.900 TL', inStock: true },
  { id: 5, name: '24 Suave Sunstone (6 g)', hex: '#ffb794', price: '2.900 TL', inStock: true },
  { id: 6, name: '37 High Peach (6 g)', hex: '#ff7f7f', price: '2.900 TL', inStock: true },
  { id: 7, name: '42 Pink Haze (6 g)', hex: '#fce4ec', price: '2.900 TL', inStock: true },
  { id: 8, name: '44 Nude Lavallière (5 g)', hex: '#bd6c7d', price: '2.900 TL', inStock: true },
  { id: 9, name: '20 Light', hex: '#fce4ec', price: '2.900 TL', inStock: true },
  { id: 10, name: '22 Fuchsia', hex: '#ff80ab', price: '2.900 TL', inStock: true },
]

// FONKSİYONLAR 

const currentVariantName = () => {
  const color = colors.find(c => c.id === selectedColorId.value)
  return color ? color.name : ''
}

const selectColor = (id) => {
  selectedColorId.value = id
  isColorModalOpen.value = false
}

const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value
}

const toggleDescription = () => {
  isDescriptionExpanded.value = !isDescriptionExpanded.value
}

const thumbnails = [anaResim, resim1, resim2]
const currentMainImage = ref(anaResim)
const changeMainImage = (clickedImage) => {
  currentMainImage.value = clickedImage
}
</script>

<template>
  <div class="product-page">
    
    <div class="breadcrumb">
      <span>Ana Sayfa</span> / <span>Makyaj</span> / <span>Yüz</span> / <strong>Allık</strong>
    </div>

    <div class="product-container">
      
      <div class="gallery-section">
        <div class="thumbnails">
          <div 
            v-for="(thumb, index) in thumbnails" 
            :key="index" 
            class="thumb-box"
            @click="changeMainImage(thumb)" 
          >
            <img :src="thumb" alt="thumb">
          </div>
        </div>

        <div class="main-image-box">
          <img :src="currentMainImage" alt="YSL Allık">
        </div>
      </div>

      <div class="info-section">
        
        <div class="brand-header">
          <h3 class="brand-name">YVES SAINT LAURENT</h3>
          <span 
            class="heart-icon" 
            :class="{ 'filled': isFavorite }"
            @click="toggleFavorite"
          >
            {{ isFavorite ? '♥' : '♡' }}
          </span>
        </div>

        <h1 class="product-title">MAKE ME BLUSH - Allık</h1>

        <div class="rating-row">
          <span class="stars">★★★★☆</span>
          <span class="review-count">84 Ürün yorumları</span>
        </div>

        <div class="description-wrapper">
          <p class="description">
            <span v-if="!isDescriptionExpanded">
              Make Me Blush allıkları şimdi pudra versiyonu ile sizlerle.
              Arttırılabilir renk özelliği ve ağırlık...
              <a href="#" class="read-more" @click.prevent="toggleDescription">Devamını oku</a>
            </span>
            <span v-else>
              Make Me Blush allıkları şimdi pudra versiyonu ile sizlerle.
              Arttırılabilir renk özelliği ve ağırlık yapmayan formülü sayesinde cildinizde doğal bir bitiş sağlar. 
              İpeksi dokusuyla gün boyu kalıcılık sunar ve cildin nefes almasına izin verir. 
              <br><br>
              Yüksek pigmentasyonu sayesinde az miktarda ürünle bile etkileyici sonuçlar elde edebilirsiniz.
              <a href="#" class="read-more" @click.prevent="toggleDescription">Daha az göster</a>
            </span>
          </p>
        </div>

        <div class="price">2.900 TL</div>

        <p class="color-discover">Ürünün farklı renklerini keşfet</p>

        <div class="selected-variant-box" @click="isColorModalOpen = true">
          <span>{{ currentVariantName() }}</span>
          <span class="arrow">›</span>
        </div>

        <div class="color-swatches">
          <div 
            v-for="color in colors" 
            :key="color.id"
            class="swatch-wrapper"
            :class="{ active: selectedColorId === color.id }"
            @click="selectedColorId = color.id"
          >
            <div class="swatch" :style="{ backgroundColor: color.hex }"></div>
          </div>
        </div>

        <button class="add-to-cart-btn">Sepete ekle</button>

        <div class="trust-badges">
          <span>Güvenli ödeme</span>
          <div class="card-icons">
            <span class="card-box visa">VISA</span>
            <span class="card-box mc">MC</span>
            <span class="card-box troy">Troy</span>
          </div>
        </div>

      </div>
    </div>

    <div v-if="isColorModalOpen" class="modal-overlay" @click.self="isColorModalOpen = false">
      <div class="modal-content">
        <div class="modal-header">
          <h3>Renk seçenekleri</h3>
          <button class="close-btn" @click="isColorModalOpen = false">✕</button>
        </div>
        <div class="modal-product-summary">
          <img :src="anaResim" class="mini-img" />
          <div class="mini-details">
            <span class="mini-brand">Yves Saint Laurent</span>
            <span class="mini-name">MAKE ME BLUSH - Allık</span>
          </div>
        </div>
        <div class="color-list-container">
          <div 
            v-for="color in colors" 
            :key="color.id" 
            class="color-option-card"
            :class="{ 'selected': selectedColorId === color.id }"
            @click="selectColor(color.id)"
          >
            <div class="option-circle" :style="{ backgroundColor: color.hex }"></div>
            <div class="option-details">
              <span class="option-name">{{ color.name }}</span>
              <div class="stock-status">
                <span class="dot" :class="color.inStock ? 'green-dot' : 'red-dot'"></span>
                <span class="status-text">{{ color.inStock ? 'Stokta' : 'Stokta yok' }}</span>
              </div>
            </div>
            <div class="option-price">{{ color.price }}</div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>
//Güvenli Ödeme İkonları ve Renk Seçim Modalı
<style scoped>
.product-page { font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; color: #000; padding: 20px; background-color: white; }
.breadcrumb { font-size: 12px; color: #666; margin-bottom: 20px; }
.product-container { display: flex; gap: 40px; }
.gallery-section { display: flex; gap: 20px; width: 50%; }
.thumbnails { display: flex; flex-direction: column; gap: 10px; }
.thumb-box { width: 60px; height: 60px; border: 1px solid #eee; cursor: pointer; transition: border-color 0.2s; }
.thumb-box:hover { border-color: #000; }
.thumb-box img { width: 100%; height: 100%; object-fit: cover; }
.main-image-box { flex: 1; background-color: #fff; display: flex; align-items: center; justify-content: center; }
.main-image-box img { max-width: 100%; max-height: 500px; object-fit: contain; }
.info-section { width: 40%; display: flex; flex-direction: column; }
.brand-header { display: flex; justify-content: space-between; align-items: center; }
.brand-name { font-size: 14px; text-decoration: underline; font-weight: 600; letter-spacing: 1px; margin: 0; }

.heart-icon { font-size: 24px; cursor: pointer; user-select: none; transition: transform 0.2s; }
.heart-icon:active { transform: scale(1.2); }
.heart-icon.filled { color: black; }

.product-title { font-size: 24px; font-weight: 700; margin: 10px 0; }
.rating-row { display: flex; align-items: center; gap: 10px; font-size: 14px; margin-bottom: 15px; }
.description { font-size: 14px; line-height: 1.5; color: #333; margin-bottom: 20px; }
.read-more { text-decoration: underline; color: #000; font-weight: 600; cursor: pointer; margin-left: 5px; }
.price { font-size: 22px; font-weight: 700; margin-bottom: 20px; }
.color-discover { font-size: 14px; margin-bottom: 10px; }
.selected-variant-box { border: 1px solid #ddd; padding: 15px; border-radius: 4px; display: flex; justify-content: space-between; align-items: center; font-weight: 700; font-size: 14px; margin-bottom: 20px; cursor: pointer; transition: background 0.2s; }
.selected-variant-box:hover { background-color: #f9f9f9; }
.color-swatches { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 30px; }
.swatch-wrapper { width: 32px; height: 32px; border-radius: 50%; padding: 2px; border: 1px solid transparent; cursor: pointer; }
.swatch-wrapper.active { border: 1px solid #000; }
.swatch { width: 100%; height: 100%; border-radius: 50%; border: 1px solid #eee; }

/* sepete ekle butonum */
.add-to-cart-btn { 
  background-color: #000; 
  color: #fff; 
  border: none; 
  width: 100%; 
  padding: 18px; 
  font-size: 16px; 
  font-weight: 700; 
  cursor: pointer; 
  transition: all 0.1s ease; 
  border-radius: 4px; 
}

/* Basma Efekti */
.add-to-cart-btn:active {
  transform: scale(0.97); 
  background-color: #333; 
}


.trust-badges { margin-top: auto; display: flex; justify-content: space-between; align-items: center; padding-top: 20px; }
.card-icons { display: flex; gap: 5px; }
.card-box { border: 1px solid #ddd; padding: 2px 5px; font-size: 10px; font-weight: bold; border-radius: 2px; }
.visa { background: #1a1f71; color: white; }
.mc { background: #eb001b; color: white; }
.troy { background: #00afda; color: white; }

.modal-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0, 0, 0, 0.5); display: flex; justify-content: flex-end; z-index: 9999; }
.modal-content { width: 450px; background: white; height: 100%; padding: 20px; overflow-y: auto; box-shadow: -5px 0 15px rgba(0,0,0,0.1); display: flex; flex-direction: column; }
.modal-header { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid #eee; padding-bottom: 15px; margin-bottom: 20px; }
.modal-header h3 { font-size: 18px; font-weight: 800; margin: 0; }
.close-btn { background: none; border: none; font-size: 24px; cursor: pointer; font-weight: bold; }
.modal-product-summary { display: flex; align-items: center; gap: 15px; margin-bottom: 30px; }
.mini-img { width: 50px; height: 50px; object-fit: contain; }
.mini-details { display: flex; flex-direction: column; }
.mini-brand { font-size: 12px; font-weight: 600; }
.mini-name { font-size: 14px; font-weight: 800; }
.color-list-container { display: flex; flex-direction: column; gap: 12px; }
.color-option-card { display: flex; align-items: center; border: 1px solid #ddd; padding: 15px; border-radius: 8px; cursor: pointer; transition: all 0.2s; }
.color-option-card:hover { border-color: #999; }
.color-option-card.selected { border: 2px solid black; }
.option-circle { width: 24px; height: 24px; border-radius: 50%; margin-right: 15px; border: 1px solid #eee; }
.option-details { flex: 1; }
.option-name { font-size: 14px; font-weight: 600; display: block; margin-bottom: 4px; }
.stock-status { display: flex; align-items: center; gap: 6px; font-size: 12px; color: #666; }
.dot { width: 8px; height: 8px; border-radius: 50%; }
.green-dot { background-color: #76c043; }
.red-dot { background-color: #d1245e; }
.option-price { font-weight: 800; font-size: 14px; }
</style>