<!-- Descripción
 Este componente es el espacio donde va la descripción de un curso, aquí dentro se puede ver el
 texto de descripción, la variable se obtiene a través de App.vue -->
<template>
  <div class="content-rectangle">
    <h4 v-if="title" class="content-title">{{ title }}</h4>
    <p v-if="content" class="content-text">{{ content }}</p>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'ContentRectangle',
  props: {
    title: {
      type: String,
      default: ''
    },
    content: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped>
.content-rectangle {
  width: 1074px;
  height: 90%;
  background-color: var(--color-white);
  border-radius: var(--card-border-radius);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.content-title {
  font-family: 'Inter', sans-serif;
  font-size: 18px;
  font-weight: 600;
  color: var(--color-black);
  margin: 0;
}

.content-text {
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  color: var(--color-black);
  line-height: 1.5;
  margin: 0;
  flex: 1;
}

/* Responsive */
@media (max-width: 768px) {
  .content-rectangle {
    width: 100%;
    height: auto;
    min-height: 200px;
    padding: 15px;
  }
  
  .content-title {
    font-size: 16px;
  }
  
  .content-text {
    font-size: 13px;
  }
}

@media (max-width: 480px) {
  .content-rectangle {
    padding: 12px;
    min-height: 150px;
  }
  
  .content-title {
    font-size: 15px;
  }
  
  .content-text {
    font-size: 12px;
  }
}
</style>