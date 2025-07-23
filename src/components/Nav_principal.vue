<script setup>
const emit = defineEmits(['next', 'prev']);
</script>
<template>
  <button class="button esquerda" @click="emit('prev')">
    <img src="../assets/seta-esquerda.svg" alt="Download CV" />
  </button>
  <button class="button direita"  @click="emit('next')">
    <img src="../assets/seta-direita.svg" alt="Download CV" />
  </button>
</template>

<style scoped>
.esquerda {
  position: absolute;
  left: 20px;
  top: 50%;
  background-color: rgba(0, 0, 0, 0.5) !important;
  border-radius: 10px;
  padding: 10px;
  opacity: 0.2;
}
.direita {
  position: absolute;
  right: 20px;
  top: 50%;
  background-color: rgba(0, 0, 0, 0.5) !important;
  border-radius: 10px;
  padding: 10px;
  opacity: 0.2;
}
.esquerda img,
.direita img {
  width: 30px;
  height: 30px;
  transition: transform 0.3s ease;
}
.esquerda img:hover,
.direita img:hover {
  transform: scale(1.2);
  opacity: 1;
}
.esquerda:hover,
.direita:hover {
  background-color: rgba(0, 0, 0, 0.7) !important;
  opacity: 1;
}
</style>
