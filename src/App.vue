<template>
  <div id="app">
    <HeaderComponent 
      :logo="logoPath"
      :info-icon="infoIconPath"
      :profile-icon="profileIconPath"
      :button-text="headerButtonText"
    />
    
    <MenuComponent 
      :menu-items="menuItems"
      :active-item="activeMenuItem"
      @menu-change="handleMenuChange"
    />
    
    <main class="main-content">
      <div class="container">
        <SliderComponent 
          :cards="sliderCards"
          :left-arrow="leftArrowPath"
          :right-arrow="rightArrowPath"
        />
      </div>
    </main>
    
    <FooterComponent 
      :left-text="footerLeftText"
      :center-text="footerCenterText"
      :right-text="footerRightText"
    />
  </div>
</template>

<script>
import HeaderComponent from './components/Header.vue'
import MenuComponent from './components/Menu.vue'
import FooterComponent from './components/Footer.vue'
import SliderComponent from './components/Slider.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MenuComponent,
    FooterComponent,
    SliderComponent
  },
  data() {
    return {
      logoPath: './src/assets/logo.svg',
      infoIconPath: './src/assets/info.svg',
      profileIconPath: './src/assets/perfil.svg',
      leftArrowPath: './src/assets/izq.svg',
      rightArrowPath: './src/assets/der.svg',
      
      headerButtonText: 'PERFIL',
      menuItems: ['INICIO', 'MATERIAL', 'COMUNIDAD', 'FOROS', 'CALENDARIO'],
      footerLeftText: 'AYUDA',
      footerCenterText: 'TÉRMINOS DE SERVICIO',
      footerRightText: 'POLITICA DE PRIVACIDAD',
      
      // Estado
      activeMenuItem: 0,
      
      sliderCards: [
        {
          title: 'ÁLGEBRA B',
          subtitle: 'Carlos Vidales',
          content: 'El álgebra es la rama de las matemáticas que utiliza símbolos (letras) para representar números y cantidades desconocidas, permitiendo estudiar las operaciones aritméticas y las relaciones numéricas de forma general.',
          image: './src/assets/algebraa.jpg'
        },
        {
          title: 'MATEMÁTICAS',
          subtitle: 'Arturo Sánchez',
          content: 'Curso especializado en cálculo diferencial e integral. Incluye aplicaciones prácticas en ingeniería y ciencias. Requisitos: Matemáticas Básicas.',
          image: './src/assets/mate.jpg'        
        },
        {
          title: 'PROGRAMACIÓN WEB',
          subtitle: 'José Maria Varela',
          content: 'Desarrollo de aplicaciones web modernas usando HTML5, CSS3, JavaScript y Vue.js. Enfoque en proyectos prácticos y mejores prácticas.',
          image: './src/assets/web.png'
        },
        {
          title: 'FÍSICA',
          subtitle: 'Ivan Dávila Puente',
          content: 'Fundamentos de mecánica clásica, termodinámica y electromagnetismo. Laboratorios virtuales y experimentos prácticos incluidos.',
          image: './src/assets/fisica.jpg'        
        },
        {
          title: 'INGLÉS',
          subtitle: 'Alberto López',
          content: 'Desarrollo de habilidades lingüísticas para contextos académicos. Enfoque en writing académico, presentaciones y comprensión de textos especializados.',
          image: './src/assets/ingles.png'
        }
      ]
    }
  },
  methods: {
    handleMenuChange(index) {
      this.activeMenuItem = index;
      console.log('Menú cambiado a:', this.menuItems[index]);
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
