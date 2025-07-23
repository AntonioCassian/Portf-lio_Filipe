<template>
  <div class="sobre-mim">
    <h2 class="sobre">Experiencia</h2>
    <p class="sobre-texto">
      Sou um Analista de Testes apaixonado por garantir a qualidade e a
      confiabilidade dos sistemas. Com experiência em testes manuais e
      automatizados, busco sempre aprimorar os processos de teste e contribuir
      para o sucesso dos projetos.
    </p>
  </div>
</template>

<style scoped>
.sobre-mim {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin-top: 20px;
  height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  max-height: 600px;
  
}

.sobre {
  font-size: 2rem;
  margin-bottom: 1rem;
}
.sobre-texto {
  font-size: 1.2rem;
  line-height: 1.5;
}

.sobre-mim::-webkit-scrollbar {
  width: 6px;
}

.sobre-mim::-webkit-scrollbar-track {
  background: transparent; 
}


.sobre-mim::-webkit-scrollbar-thumb {
  background-color: rgba(100, 100, 100, 0.4); /* Cor da barra */
  border-radius: 4px; /* Arredondamento */
}

.sobre-mim::-webkit-scrollbar-thumb:hover {
  background-color: rgba(100, 100, 100, 0.6);
}
</style>
