<script setup>
import { shallowRef } from 'vue'

// 1. ELİNDEKİ TÜM BİLEŞENLERİ BURAYA ÇAĞIRIYORUZ
// (Dosya isimlerin TheHeader ve TheFooter olarak güncellediğini varsayıyorum)
import ProductDetail from './components/organisms/ProductDetail.vue'
import CartPage from './components/organisms/CartPage.vue'
import RegisterForm from './components/organisms/RegisterForm.vue'
import LoginForm from './components/organisms/LoginForm.vue'
import TheHeader from './components/organisms/TheHeader.vue'
import TheFooter from './components/organisms/TheFooter.vue'
import TopBanner from './components/molecules/TopBanner.vue'
import TrendingProducts from './components/organisms/TrendingProducts.vue'
import AccountSidebar from './components/organisms/AccountSidebar.vue'
import CampaignGrid from './components/organisms/CampaignGrid.vue'
import AddToCartModal from './components/organisms/AddToCartModal.vue'
import MainNavigation from './components/molecules/MainNavigation.vue'

// Eğer Slider dosyasını oluşturduysan aşağıdaki yorumu kaldırabilirsin:
// import HeroSlider from './components/organisms/HeroSlider.vue'

// 2. SOL MENÜDE GÖZÜKECEK LİSTE
const componentList = [
{ name: 'Trend Ürünler Slider (Organism)', component: TrendingProducts },
{ name: 'Kampanyalar Grid (Organism)', component: CampaignGrid },
{ name: 'Ürün Detay Sayfası (Organism)', component: ProductDetail },  
{ name: 'Ana Header (Organism)', component: TheHeader },
{ name: 'Sepet Sayfası (Organism)', component: CartPage },  
{ name: 'Ana Footer (Organism)', component: TheFooter },
{ name: 'Sepete Eklendi Modalı (Organism)', component: AddToCartModal }, 

{ name: 'Hesabım Menüsü (Organism)', component: AccountSidebar }, 

{ name: 'Giriş Yap Formu (Organism)', component: LoginForm },
{ name: 'Üyelik Formu (Organism)', component: RegisterForm },
  // { name: 'Slider (Organism)', component: HeroSlider }, // Slider yapınca bunu açarsın
]

// 3. BAŞLANGIÇTA HANGİSİ GÖZÜKSÜN? (İlk sıradaki)
const currentComponent = shallowRef(componentList[0].component)
const currentName = shallowRef(componentList[0].name)

// 4. TIKLAYINCA DEĞİŞTİREN FONKSİYON
function selectComponent(item) {
  currentComponent.value = item.component
  currentName.value = item.name
}
</script>

<template>
  <div class="showcase-layout">
    
    <aside class="sidebar">
      <div class="sidebar-header">
        <h2>📦 Proje Vitrini</h2>
        <p>Bileşen Listesi</p>
      </div>
      
      <ul>
        <li v-for="(item, index) in componentList" :key="index">
          <button 
            @click="selectComponent(item)"
            :class="{ active: currentName === item.name }"
          >
            {{ item.name }}
          </button>
        </li>
      </ul>
    </aside>

    <main class="preview-area">
      <div class="preview-info">
        Şu an görüntülenen: <strong>{{ currentName }}</strong>
      </div>
      
      <div class="component-wrapper">
        <component :is="currentComponent" />
      </div>
    </main>

  </div>
</template>

<style>
/* Sayfa Ayarları */
body { margin: 0; padding: 0; font-family: 'Segoe UI', sans-serif; overflow: hidden; }

.showcase-layout {
  display: flex;
  height: 100vh; /* Tam ekran yüksekliği */
  width: 100vw;
}

/* --- SOL MENÜ TASARIMI --- */
.sidebar {
  width: 260px;
  background-color: #212529; /* Koyu gri */
  color: white;
  display: flex;
  flex-direction: column;
  border-right: 1px solid #333;
  flex-shrink: 0;
}

.sidebar-header {
  padding: 20px;
  background-color: #000;
  text-align: center;
  border-bottom: 1px solid #333;
}

.sidebar h2 { font-size: 18px; margin: 0; }
.sidebar p { font-size: 12px; color: #aaa; margin: 5px 0 0; }

.sidebar ul { list-style: none; padding: 0; margin: 0; }

.sidebar button {
  width: 100%;
  padding: 15px 20px;
  background: none;
  border: none;
  color: #adb5bd;
  text-align: left;
  cursor: pointer;
  font-size: 14px;
  border-bottom: 1px solid #333;
  transition: 0.2s;
}

.sidebar button:hover {
  background-color: #343a40;
  color: white;
  padding-left: 25px; /* Hover olunca hafif sağa kaysın */
}

.sidebar button.active {
  background-color: #d1245e; /* Sephora pembesi */
  color: white;
  font-weight: bold;
}

/* --- SAĞ TARAF TASARIMI --- */
.preview-area {
  flex: 1;
  background-color: #e9ecef; /* Açık gri arka plan */
  display: flex;
  flex-direction: column;
}

.preview-info {
  background-color: white;
  padding: 15px 20px;
  border-bottom: 1px solid #ddd;
  color: #495057;
  font-size: 14px;
}

.component-wrapper {
  flex: 1;
  padding: 20px;
  overflow-y: auto; /* Bileşen büyükse kaydırma çubuğu çıksın */
  background-color: white; /* Bileşenlerin zemini beyaz olsun */
  margin: 20px;
  border-radius: 8px;
  box-shadow: 0 0 15px rgba(0,0,0,0.1);
}
</style>