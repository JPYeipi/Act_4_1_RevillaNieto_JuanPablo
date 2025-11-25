<!-- Boton 
Este componente es el boton que debe servir para entrar al perfil, debería de estar dentro del 
componente de Header, se puede reutilizar si queremos hacer cualquier otro botón
Recibe el texto como variable de App.vue, y los estilos son para que sea responsivo y hover
-->

<template>
  <button 
    :class="['custom-button']"
  >
    {{ buttonText }}
  </button>
</template>

<script>
export default {
  name: 'ButtonComponent',
  props: {
    buttonText: {
      type: String,
    },
  },
}
</script>

<style scoped>
.custom-button {
  width: var(--button-width);
  height: var(--button-height);
  background-color: var(--color-primary);
  color: var(--color-white);
  border: 1px solid var(--color-black);
  border-radius: var(--border-radius);
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.custom-button:hover {
  background-color: var(--color-primary-hover);
}

@media (max-width: 768px) {
  .custom-button{
    width: 140px;
  }
  .custom-button:hover {
  background-color: var(--color-primary-hover);
}
}

@media (max-width: 480px) {
  .custom-button {
    width: 100px;
  }
  .custom-button:hover {
  background-color: var(--color-primary-hover);
}
}

</style>

