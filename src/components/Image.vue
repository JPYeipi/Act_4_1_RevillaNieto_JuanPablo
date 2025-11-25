<template>
  <div class="image-square">
    <img v-if="imageSrc" :src="imageSrc" :alt="altText" class="square-image">
    <div v-else class="placeholder">
      {{ placeholderText }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'ImageSquare',
  props: {
    imageSrc: {
      type: String,
      default: ' '
    },
    altText: {
      type: String,
      default: 'Imagen'
    },
    placeholderText: {
      type: String,
      default: 'Materia'
    }
  }
}
</script>

<style scoped>
.image-square {
  width: 130px;
  height: 130px;
  background-color: var(--color-white);
  border-radius: var(--card-border-radius);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.square-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: var(--card-border-radius);
}

.placeholder {
  color: var(--color-gray);
  font-family: 'Inter', sans-serif;
  font-size: 14px;
}

/* Responsive */
@media (max-width: 768px) {
  .image-square {
    width: 100px;
    height: 100px;
  }
}

@media (max-width: 480px) {
  .image-square {
    width: 80px;
    height: 80px;
  }
  
  .placeholder {
    font-size: 12px;
  }
}
</style>