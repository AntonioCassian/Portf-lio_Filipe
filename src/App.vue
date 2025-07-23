<script setup>
import { computed, onMounted, onUnmounted, ref } from "vue";
import Card_project from "./components/card_project.vue";
import Sobre_mim from "./components/Sobre_mim.vue";
import Linguagens from "./components/Linguagens.vue";
import { projetos } from "./lib/projetos";
import Nav_principal from "./components/Nav_principal.vue";
import Pagination from "./components/Pagination.vue";
import Experiencia from "./components/Experiencia.vue";

const currentPage = ref(1);
const itemsPage = ref(8);
const totalItems = ref(projetos.length);
const totalPages = computed(() =>
  Math.ceil(totalItems.value / itemsPage.value)
);

const windowWidth = ref(window.innerWidth);

const updateItemsPerPage = () => {
  windowWidth.value = window.innerWidth;

  if (windowWidth.value < 768) {
    itemsPage.value = 2;
  } else if (windowWidth.value < 1400) {
    itemsPage.value = 8;
  } else if (windowWidth.value > 1400) {
    itemsPage.value = 6;
  } else {
    itemsPage.value = 4;
  }
};

onMounted(() => {
  updateItemsPerPage();
  window.addEventListener("resize", updateItemsPerPage);
});

onUnmounted(() => {
  window.removeEventListener("resize", updateItemsPerPage);
});

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
};

const prevPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
};

const pagination = computed(() => {
  const start = (currentPage.value - 1) * itemsPage.value;
  const end = start + itemsPage.value;
  return projetos.slice(start, end);
});

const textPrincipal = ref(1);
const nextText = () => {
  textPrincipal.value = textPrincipal.value === 3 ? 1 : textPrincipal.value + 1;
};

const prevText = () => {
  textPrincipal.value = textPrincipal.value === 1 ? 3 : textPrincipal.value - 1;
};

// Troca automática do texto principal a cada 8 segundos
let intervalId;

const startInterval = () => {
  intervalId = setInterval(() => {
    nextText();
  }, 8000);
};

const stopInterval = () => {
  clearInterval(intervalId);
};

onMounted(() => {
  startInterval();
});

onUnmounted(() => {
  stopInterval();
});

// Pausa o intervalo ao passar o mouse na div .intro
const handleMouseEnter = () => {
  stopInterval();
};

const handleMouseLeave = () => {
  startInterval();
};
</script>

<template>
  <section class="flex section-margin">
    <div
      class="intro"
      @mouseenter="handleMouseEnter"
      @mouseleave="handleMouseLeave"
    >
      <template v-if="textPrincipal === 1">
        <Linguagens />
      </template>
      <template v-else-if="textPrincipal === 2">
        <Sobre_mim />
      </template>
      <template v-else-if="textPrincipal === 3">
        <Experiencia />
      </template>
      <Nav_principal @next="nextText" @prev="prevText" />
    </div>

    <div class="foto-wrapper">
      <!-- <img src="./assets/filipe.png" alt="" /> -->
    </div>
  </section>

  <section>
    <h2>Projetos</h2>
    <div class="section-2">
      <Card_project
        v-for="projeto in pagination"
        :key="projeto.id"
        :id="projeto.id"
        :img="projeto.img"
        :title="projeto.title"
        :description="projeto.description"
        :link="projeto.link"
      />

      <Pagination
        :currentPage="currentPage"
        :totalPages="totalPages"
        @next-page="nextPage"
        @prev-page="prevPage"
      />
    </div>
  </section>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.foto-wrapper {
  position: relative;
  flex: 1;
  height: 100%;
  background-image: url("./assets/filipe.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.6);

  -webkit-mask-image: linear-gradient(to bottom, black 60%, transparent 100%);
  mask-image: linear-gradient(to bottom, black 60%, transparent 100%);
  -webkit-mask-composite: destination-in;
  mask-composite: intersect;
}

.foto-wrapper::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    transparent 0%,
    rgba(0, 0, 0, 0.6) 100%
  );
  pointer-events: none;
}

.flex {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100%;
  gap: 3em;
}

/* .foto-wrapper::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: oklch(38% 0.189 293.745);
  clip-path: polygon(0 0, 100% 0, 100% 70%, 0 100%);
  z-index: -1;
  transform: rotate(-3deg);
  border-radius: 10px;
}*/

.foto-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 10px;
  position: relative;
  z-index: 1;
  /* mix-blend-mode: darken; */
}

.section-margin {
  margin-bottom: 4rem;
}

.section-2 {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
  padding: 2rem;
  position: relative;
}
</style>
