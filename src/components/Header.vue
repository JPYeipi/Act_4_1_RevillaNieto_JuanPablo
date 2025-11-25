<template>
  <header class="header">
    <div class="header-content">
      <div class="left-section">
        <img :src="infoIcon" alt="Información" class="icon info-icon" >
      </div>
      
      <div class="center-section">
        <img :src="logo" alt="Logo" class="logo">
      </div>
      
      

      <div class="right-section">
        <img :src="profileIcon" alt="Perfil" class="icon profile-icon" >
        <ButtonComponent 
          :button-text="buttonText" 
          class="header-button"
        />
      </div>
    </div>
  </header>
</template>

<script>
import ButtonComponent from './Button.vue';

export default {
  name: 'HeaderComponent',
  components: {
    ButtonComponent
  },
  props: {
    logo: {
      type: String,
      required: true
    },
    infoIcon: {
      type: String,
      required: true
    },
    profileIcon: {
      type: String,
      required: true
    },
    buttonText: {
      type: String,
      default: 'Iniciar Sesión'
    }
  },
 
}
</script>

<style scoped>
.header {
  width: 100%;
  height: var(--header-height);
  background-color: var(--color-white);
  border-bottom: 1px solid var(--color-black);
  display: flex;
  align-items: center;
  justify-content: center;
}

.header-content {
  width: 100%;
  max-width: 1350px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px;
}

.left-section, .right-section {
  display: flex;
  align-items: center;
  gap: 20px;
}

.center-section {
  flex: 1;
  display: flex;
  justify-content: center;
}

.logo {
  height: 140px;
  width: auto;
}

.icon {
  width: 50px;
  height: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.profile-icon:hover {
  filter: brightness(0) saturate(100%) invert(40%) sepia(90%) saturate(1500%) hue-rotate(200deg);
}

.info-icon:hover {
  opacity: 0.7;
}

.header-button {
  margin-right: 10px;
}

@media (max-width: 768px) {
  .header-content {
    padding: 0 15px;
  }
  
  .logo {
    height: 60px;
  }
  
  .icon {
    width: 28px;
    height: 28px;
  }
}

@media (max-width: 480px) {
  .header-content {
    padding: 0 10px;
  }
  
  .logo {
    height: 50px;
  }
  
  .left-section, .right-section {
    gap: 10px;
  }
}
</style>