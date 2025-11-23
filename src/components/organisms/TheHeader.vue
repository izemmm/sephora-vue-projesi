<script setup>
import TopBanner from '../molecules/TopBanner.vue';
import MainNavigation from '../molecules/MainNavigation.vue';
</script>

<template>
  <header>
    <TopBanner />

    <div class="middle-bar container">
      <div class="logo">
        <h1>SEPHORA</h1>
      </div>

      <div class="search-bar">
        <div class="search-icon-wrapper">
          <svg viewBox="0 0 24 24" width="24" height="24" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
        </div>
        <input type="text" placeholder="Ürün, marka, kategori ara..." />
      </div>

      <div class="actions">
        
        <div class="action-item">
          <svg viewBox="0 0 24 24" width="24" height="24" stroke="currentColor" stroke-width="2" fill="none"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path><circle cx="12" cy="10" r="3"></circle></svg>
          <span>Mağazalar ve Servisler</span>
        </div>

        <div class="action-item">
          <svg viewBox="0 0 24 24" width="24" height="24" stroke="currentColor" stroke-width="2" fill="none"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg>
          <span>Hesabım</span>
        </div>

        <div class="icon-wrapper">
          <svg viewBox="0 0 24 24" width="26" height="26" stroke="currentColor" stroke-width="2" fill="none"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path></svg>
          <span class="badge">14</span>
        </div>

        <div class="icon-wrapper">
          <svg viewBox="0 0 24 24" width="26" height="26" stroke="currentColor" stroke-width="2" fill="none"><path d="M6 2L3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"></path><line x1="3" y1="6" x2="21" y2="6"></line><path d="M16 10a4 4 0 0 1-8 0"></path></svg>
          <span class="badge">6</span>
        </div>

      </div>
    </div>

    <MainNavigation />
  </header>
</template>

<style scoped>
.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 20px;
}

.middle-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 25px 0;
}

/* LOGO STİLİ */
.logo h1 {
  letter-spacing: 4px;
  font-size: 32px;
  margin: 0;
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  font-weight: 500;
  cursor: pointer;
  transition: transform 0.1s ease; 
}

/* Logo Basma Efekti */
.logo h1:active {
  transform: scale(0.95);
}

/* ARAMA ÇUBUĞU */
.search-bar {
  display: flex;
  align-items: center;
  background-color: #f2f2f2;
  padding: 12px 20px;
  border-radius: 99px;
  width: 35%;
  position: relative;
}

.search-icon-wrapper {
  display: flex;
  align-items: center;
  color: #000;
  margin-right: 10px;
}

.search-bar input {
  border: none;
  background: transparent;
  outline: none;
  width: 100%;
  font-size: 14px;
  font-weight: 500;
  color: #666;
}

/* SAĞ İKONLAR ALANI */
.actions {
  display: flex;
  align-items: center;
  gap: 25px;
  font-size: 14px;
  font-weight: 600;
  font-family: sans-serif;
}

.action-item {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  white-space: nowrap;
  transition: transform 0.1s ease, color 0.2s; 
}

/* Action Item Hover & Active */
.action-item:hover {
  color: #555; 
}
.action-item:active {
  transform: scale(0.95); 
  color: #000;
}

/* İkon + Badge */
.icon-wrapper {
  position: relative;
  cursor: pointer;
  display: flex;
  align-items: center;
  transition: transform 0.1s ease;
}

/* İkon Basma Efekti */
.icon-wrapper:active {
  transform: scale(0.90);
}

/* Bildirim  */
.badge {
  position: absolute;
  top: -6px;
  right: -8px;
  background-color: #d1245e;
  color: white;
  font-size: 10px;
  font-weight: bold;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid white;
}
</style>