<!-- Menu
 Este componente se utiliza en todas las vistas, nos ayuda a navegar entre las vistas principales
 de la página web -->
<template>
  <nav class="menu">
    <div class="menu-container desktop-menu">
      <button
        v-for="(item, index) in menuItems"
        :key="index"
        :class="['menu-item', { 'active': activeItem === index }]"
        @click="handleMenuClick(index)"
      >
        {{ item }}
      </button>
    </div>

    <div class="mobile-menu">
      <button class="hamburger-button" @click="toggleMobileMenu">
        <span class="hamburger-icon"></span>
        <span class="hamburger-icon"></span>
        <span class="hamburger-icon"></span>
      </button>
      
      <div v-if="isMobileMenuOpen" class="mobile-menu-items">
        <button
          v-for="(item, index) in menuItems"
          :key="index"
          :class="['mobile-menu-item', { 'active': activeItem === index }]"
          @click="handleMobileMenuClick(index)"
        >
          {{ item }}
        </button>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'MenuComponent',
  props: {
    menuItems: {
      type: Array,
      default: () => ['INICIO', 'MATERIAL', 'COMUNIDAD', 'FOROS', 'CALENDARIO']
    },
    activeItem: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      isMobileMenuOpen: false
    }
  },
  methods: {
    handleMenuClick(index) {
      this.$emit('menu-change', index);
    },
    handleMobileMenuClick(index) {
      this.isMobileMenuOpen = false;
      this.$emit('menu-change', index);
    },
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    }
  },
  emits: ['menu-change']
}
</script>

<style scoped>
.menu {
  width: 100%;
  min-height: var(--menu-height);
  display: flex;
  justify-content: center;
  background-color: var(--color-white);
  margin-bottom: 30px;
}

.desktop-menu {
  width: 100%;
  max-width: 1350px;
  height: 100%;
  display: flex;
  border: 1px solid var(--color-black);
  border-radius: 0;
}

.menu-item {
  flex: 1;
  height: var(--menu-height);
  background-color: var(--color-secondary);
  color: var(--color-white);
  border: none;
  border-right: 1px solid var(--color-black);
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 600;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 0.3s ease;
  letter-spacing: 0.5px;
}

.menu-item:last-child {
  border-right: none;
}

.menu-item:hover {
  background-color: var(--color-primary-hover);
}

.menu-item.active {
  background-color: var(--color-primary-hover);
}

.mobile-menu {
  display: none;
  width: 100%;
  position: relative;
}

.hamburger-button {
  width: 100%;
  height: var(--menu-height);
  background-color: var(--color-secondary);
  border: 1px solid var(--color-black);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 4px;
  cursor: pointer;
  padding: 10px;
}

.hamburger-icon {
  width: 25px;
  height: 3px;
  background-color: var(--color-white);
  transition: all 0.3s ease;
}

.hamburger-button:hover .hamburger-icon {
  background-color: var(--color-primary-hover);
}

.mobile-menu-items {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background-color: var(--color-white);
  border: 1px solid var(--color-black);
  border-top: none;
  z-index: 1000;
  display: flex;
  flex-direction: column;
}

.mobile-menu-item {
  width: 100%;
  height: 50px;
  background-color: var(--color-secondary);
  color: var(--color-white);
  border: none;
  border-bottom: 1px solid var(--color-black);
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 600;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 0.3s ease;
  letter-spacing: 0.5px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.mobile-menu-item:last-child {
  border-bottom: none;
}

.mobile-menu-item:hover {
  background-color: var(--color-primary-hover);
}

.mobile-menu-item.active {
  background-color: var(--color-primary-hover);
}


@media (max-width: 1024px) {
  .desktop-menu {
    flex-wrap: wrap;
    height: auto;
  }
  
  .menu-item {
    flex: 1 0 33.333%;
    height: calc(var(--menu-height) - 10px);
    border-right: 1px solid var(--color-black);
    border-bottom: 1px solid var(--color-black);
    font-size: 14px;
  }
  
  .menu-item:nth-child(3) {
    border-right: none;
  }
  
  .menu-item:nth-child(4),
  .menu-item:nth-child(5) {
    flex: 1 0 50%;
    height: calc(var(--menu-height) - 10px);
  }
  
  .menu-item:nth-child(4) {
    border-right: 1px solid var(--color-black);
  }
  
  .menu-item:nth-child(5) {
    border-right: none;
  }
  
  .menu-item:nth-child(4),
  .menu-item:nth-child(5) {
    border-bottom: none;
  }
}

@media (max-width: 768px) {
  .desktop-menu {
    display: none;
  }
  
  .mobile-menu {
    display: block;
    padding: 0 15px;
  }
  
  .hamburger-button {
    max-width: 300px;
    margin: 0 auto;
  }
}

@media (max-width: 480px) {
  .mobile-menu {
    padding: 0 10px;
  }
  
  .hamburger-button {
    max-width: 100%;
  }
  
  .mobile-menu-item {
    height: 45px;
    font-size: 14px;
  }
}

.hamburger-button.open .hamburger-icon:nth-child(1) {
  transform: rotate(45deg) translate(6px, 6px);
}

.hamburger-button.open .hamburger-icon:nth-child(2) {
  opacity: 0;
}

.hamburger-button.open .hamburger-icon:nth-child(3) {
  transform: rotate(-45deg) translate(6px, -6px);
}
</style>