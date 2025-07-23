<script lang="js" setup>
defineProps({
  id: Number,
  img: String,
  title: String,
  description: String,
  link: String
})
</script>

<template>
  <div class="card" :style="{ backgroundImage: `url(${img})` }">
    <a :href="link" class="card-content" target="_blank">
      <h2>{{ title }}</h2>
      <p>
        {{ description }}
      </p>
    </a>
  </div>
</template>

<style scoped>
.card {
  width: 250px;
  height: 250px;
  position: relative;
  /* background: linear-gradient(145deg, #2e2e2e, #1c1c1c); */
  /* border: 18px solid transparent; */
  /* border-image: url('../assets/wood-textura.svg') 40 round; */

  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.6);
  border-radius: 20px;
  color: #f5f5f5;

  /* background-image: url("https://cdn-icons-png.flaticon.com/512/9064/9064483.png"); */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  cursor: pointer;

  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card h2 {
  font-size: 1em;
  margin: 0.5em 0;
  display: none;
}

.card p {
  font-size: 0.8em;
  color: #f0f0f0;
  margin: 0.5em 0;
  display: none;
}

.card h2,
.card p {
  position: relative;
  z-index: 2;
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0.5);
  /* transform: scale(1.05);
  transition: transform 0.3s ease; */
}
.card:hover h2,
.card:hover p {
  display: block;
  transition: display 0.3s ease;
  color: #f0f0f0;
  opacity: 1;
  visibility: visible;
}

.card::before {
  content: "";
  position: absolute;
  inset: 0;
  background-color: rgba(0, 0, 0, 0);
  transition: background-color 0.3s ease;
  z-index: 1;
}

/* escurece no hover */
.card:hover::before {
  background-color: rgba(0, 0, 0, 0.5); /* escurece no hover */
}

.project-image {
  width: 100px;
  height: 100px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);
}

.card-content {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0,0,0,0.6);
  padding: 10px;
  text-align: center;
  color: white;
  text-decoration: none;
}
</style>
