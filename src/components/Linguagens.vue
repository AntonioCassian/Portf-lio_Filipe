<template>
     <h1>Filipe Gabriel <span>_</span></h1>
        <p>Analista de Testes</p>
        <div class="linguagens">
          <img src="../assets/python.svg" alt="Python" />
          <img src="../assets/javascript.svg" alt="JavaScript" />
        </div>

        <div class="redes-sociais">
          <a href="http://">
            <img src="../assets/linkedin.svg" alt="Linkedin" />
          </a>
          <a href="http://">
            <img src="../assets/github.svg" alt="Github" />
          </a>
        </div>
</template>
<style scoped>
.intro h1 {
  /* font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; */
  font-family: 'Roboto Mono', monospace;
  font-weight: 700;
  font-size: 4.5rem;
  margin: 0;
  color: #f0f0f0;
  position: relative;
}

.intro h1 span {
  color: #e7e7e7;
  font-weight: bold;
  font-size: 4.5rem;
  position: absolute;
  margin-left: 8px;
  line-height: normal;
  animation: blink 1.2s steps(2, start) infinite;
}

.intro p {
  font-size: 3.5rem;
  color: #bbb;
  margin-top: 0.5rem;
}

.linguagens {
  display: flex;
  justify-content: center;
  margin-top: 20px;
  gap: 1em;
  height: 60px;
}

.redes-sociais {
  display: flex;
  gap: 2em;
  justify-content: center;
  margin-top: 6rem;
}

.redes-sociais img {
  width: 50px;
  height: 50px;
  transition: transform 0.3s ease;
}

.redes-sociais img:hover {
  transform: scale(1.1);
}

</style>