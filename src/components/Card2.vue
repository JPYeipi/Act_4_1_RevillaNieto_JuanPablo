<template>
  <div class="inner-card">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'InnerCard'
}
</script>

<style scoped>
.inner-card {
  width: 100%;
  max-width: 1151px;
  height: 480px;
  background-color: var(--color-background);
  border-radius: var(--card-border-radius);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  position: relative;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .inner-card {
    height: 400px;
  }
}

@media (max-width: 480px) {
  .inner-card {
    height: 350px;
  }
}
</style>