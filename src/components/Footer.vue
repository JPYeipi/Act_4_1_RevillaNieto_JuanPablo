<!-- Footer
 Este componente es el footer de toda la página, es reutilizable, ya que el footer se debería de 
 poder ver en cualquier vista de la página, solo nos da información abajo -->
<template>
  <footer class="footer">
    <div class="footer-content">
      <span class="footer-text">{{ leftText }}</span>
      <span class="separator">|</span>
      <span class="footer-text">{{ centerText }}</span>
      <span class="separator">|</span>
      <span class="footer-text">{{ rightText }}</span>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterComponent',
  props: {
    leftText: {
      type: String,
    },
    centerText: {
      type: String,
    },
    rightText: {
      type: String,
    }
  }
}
</script>

<style scoped>
.footer {
  width: 100%;
  height: var(--footer-height);
  background-color: var(--color-primary-hover);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: auto;
}

.footer-content {
  display: flex;
  align-items: center;
  gap: 20px;
  color: var(--color-white);
  font-family: 'Inter', sans-serif;
  font-size: 14px;
}

.separator {
  color: var(--color-white);
  font-weight: 300;
}

.footer-text {
  text-align: center;
}

@media (max-width: 768px) {
  .footer-content {
    gap: 15px;
    font-size: 13px;
  }
}

@media (max-width: 480px) {
  .footer-content {
    flex-direction: column;
    gap: 5px;
    font-size: 12px;
  }
  
  .separator {
    display: none;
  }
}
</style>