<!-- Title
 Este componente es simplemente un cuadro de texto, es bastante reutilizable, ya que es responsivo
 solo es texto. -->
<template>
  <div class="text-rectangle">
    <h3 v-if="title" class="rectangle-title">{{ title }}</h3>
    <p v-if="content" class="rectangle-content">{{ content }}</p>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'TextRectangle',
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
.text-rectangle {
  width: 799px;
  height: 48px;
  background-color: var(--color-white);
  border-radius: var(--card-border-radius);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  padding: 12px 20px;
  display: flex;
  align-items: center;
}

.rectangle-title {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 600;
  color: var(--color-black);
  margin: 0;
}

.rectangle-content {
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  color: var(--color-black);
  margin: 0;
}

/* Responsive */
@media (max-width: 908px) {
  .text-rectangle {
    width: 100%;
    height: auto;
    min-height: 40px;
    padding: 10px 15px;
  }
  
  .rectangle-title {
    font-size: 15px;
  }
  
  .rectangle-content {
    font-size: 13px;
  }
}

@media (max-width: 480px) {
  .text-rectangle {
    padding: 8px 12px;
  }
  
  .rectangle-title {
    font-size: 14px;
  }
  
  .rectangle-content {
    font-size: 12px;
  }
}
</style>