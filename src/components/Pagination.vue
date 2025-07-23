<script setup>
const props = defineProps({
  currentPage: Number,
  totalPages: Number,
});
const emit = defineEmits(["next-page", "prev-page"]);
</script>
<template>
  <div class="paginations-controller">
    <button class="prev button-controller" @click="emit('prev-page')">
      <img src="../assets/arrow-left.svg" alt="Prev" />
    </button>
    <span class="page-number">{{ currentPage }}</span>
    <span class="separator">/</span>
    <span class="totals">{{ totalPages }}</span>
    <button class="next button-controller" @click="emit('next-page')">
      <img src="../assets/arrow-right.svg" alt="Next" />
    </button>
    <!-- <span class="separator">|</span>
      <span class="total-items">Total: {{ totalItems }}</span> -->
  </div>
</template>
<style scoped>
.paginations-controller {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  position: absolute;
  bottom: 20px;
  right: 0%;
  z-index: 10;
}

.button-controller {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  background-color: transparent;
  border: none;
  cursor: pointer;
  width: 20px;
  height: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  padding: 20px;
}
.button-controller:hover {
  transform: scale(1.1);
  transition: transform 0.3s ease;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
}
.button-controller:focus {
  outline: none;
}
.button-controller img {
  width: 20px;
  height: 20px;
  color: #fff;
}
</style>
