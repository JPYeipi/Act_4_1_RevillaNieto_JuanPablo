<template>
  <div class="card-background">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'CardBackground'
}
</script>

<style scoped>
.card-background {
  width: 100%;
  max-width: 1302px;
  height: 638px;
  background-color: var(--color-white);
  border-radius: var(--card-border-radius);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  padding: 30px;
  position: relative;
}

@media (max-width: 768px) {
  .card-background {
    height: auto;
    min-height: 500px;
    padding: 20px;
  }
}

@media (max-width: 480px) {
  .card-background {
    padding: 15px;
    min-height: 400px;
  }
}
</style>