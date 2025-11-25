<template>
  <div id="app">
    <HeaderComponent 
      :logo="logoPath"
      :info-icon="infoIconPath"
      :profile-icon="profileIconPath"
      :button-text="headerButtonText"
    />
  
    
    <FooterComponent 
      :left-text="footerLeftText"
      :center-text="footerCenterText"
      :right-text="footerRightText"
    />
  </div>
</template>

<script>
import HeaderComponent from './components/Header.vue'
import FooterComponent from './components/Footer.vue'


export default {
  name: 'App',
  components: {
    HeaderComponent,
    FooterComponent
  },
  data() {
    return {
      logoPath: './src/assets/logo.svg',
      infoIconPath: './src/assets/info.svg',
      profileIconPath: './src/assets/perfil.svg',
      
      headerButtonText: 'Iniciar Sesión',
      footerLeftText: 'AYUDA',
      footerCenterText: 'TÉRMINOS DE SERVICIO',
      footerRightText: 'POLITICA DE PRIVACIDAD',
    }
  }
}
</script>

<style>
.main-content {
  flex: 1;
  padding: 20px;
  display: flex;
  justify-content: center;
}

.container {
  width: 100%;
  max-width: 1400px;
  display: flex;
  justify-content: center;
}

@media (max-width: 768px) {
  .main-content {
    padding: 15px;
  }
}

@media (max-width: 480px) {
  .main-content {
    padding: 10px;
  }
}
</style>
