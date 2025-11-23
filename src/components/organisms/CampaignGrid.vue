<script setup>

import img1 from '@/assets/kampanya-1.png'
import img2 from '@/assets/kampanya-2.png'
import img3 from '@/assets/kampanya-3.png'
import img4 from '@/assets/kampanya-4.png'


import img1Hover from '@/assets/kampanya-1-hover.png'
import img2Hover from '@/assets/kampanya-2-hover.png'
import img3Hover from '@/assets/kampanya-3-hover.png'
import img4Hover from '@/assets/kampanya-4-hover.png'


const campaigns = [
  { id: 1, image: img1, hoverImage: img1Hover, alt: 'Kampanya 1' },
  { id: 2, image: img2, hoverImage: img2Hover, alt: 'Kampanya 2' },
  { id: 3, image: img3, hoverImage: img3Hover, alt: 'Kampanya 3' },
  { id: 4, image: img4, hoverImage: img4Hover, alt: 'Kampanya 4' }
]
</script>

<template>
  <div class="campaign-section">
    <div class="header">
      <h2>KAMPANYALAR</h2>
    </div>

    <div class="grid-container">
      <div 
        v-for="campaign in campaigns" 
        :key="campaign.id" 
        class="campaign-card"
      >
        <img :src="campaign.image" :alt="campaign.alt" class="img-normal" />
        
        <img :src="campaign.hoverImage" :alt="campaign.alt" class="img-hover" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.campaign-section {
  padding: 40px 20px;
  max-width: 1200px;
  margin: 0 auto;
  font-family: 'Helvetica Neue', Arial, sans-serif;
}

.header h2 {
  font-size: 24px;
  font-weight: 800;
  margin-bottom: 30px;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* Grid Düzeni: 2 Sütun */
.grid-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr); /* Yan yana 2 tane */
  gap: 30px; 
}

/* Kart Kutusu */
.campaign-card {
  position: relative; /* Resimlerin üst üste binmesi için  */
  width: 100%;
  height: 0;
  padding-bottom: 56.25%; /*  dikdörtgen olması için */
  overflow: hidden;
  border-radius: 4px;
  cursor: pointer;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

/* Resim Ayarları */
.campaign-card img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover; /* Resmi kutuya sığdırmak için */
  transition: opacity 0.4s ease-in-out; 
}

/* Normal Resim varsayılan olarak görünür */
.img-normal {
  opacity: 1;
  z-index: 1;
}

/* Hover Resim varsayılan olarak gizli */
.img-hover {
  opacity: 0;
  z-index: 2; /* Diğerinin üstünde durmalı */
}

/* mousela üzerine gelince*/
.campaign-card:hover .img-hover {
  opacity: 1; /* Gizli resim görünür oluyo */
}

/* Mobilde tek sütuna düşsün diye*/
@media (max-width: 768px) {
  .grid-container {
    grid-template-columns: 1fr;
  }
}
</style>