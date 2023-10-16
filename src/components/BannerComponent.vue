<script setup>
const props = defineProps(['mode', 'carouselOnMobile', 'items'])

function getCTAObject(items) {
  return JSON.parse(items).filter(obj => obj.type === "cta")[0]
}

function getImageObject(items, aspectRatio) {
  return JSON.parse(items)
    .filter(obj => obj.type === "image")
    .filter(img => img.aspectRatio === aspectRatio)[0];
}

function openURL(url) {
  window.open(url, '_blank', 'noreferrer');
}

</script>

<template>
  <div v-if="carouselOnMobile === 'true'" class="grid-container">
    <div class="cta-div">
        <h1>{{ getCTAObject(items).title }}</h1>
        <div class="cta-button" @click="openURL(getCTAObject(items).link)">{{ getCTAObject(items).button }}</div>
    </div>
    <div v-for="item in JSON.parse(items).filter(obj => obj.type === 'image')" class="grid-item">
      <img v-bind:src="item.src" @click="openURL(item.link)"/>
    </div>
  </div>

  <div v-else-if="mode === 'rectangle'" class="rectangle">
    <img v-bind:src="getImageObject(items, 'square').src" @click="openURL(getImageObject(items, 'square').link)"/>
      <div class="cta-div">
        <h1>{{ getCTAObject(items).title }}</h1>
        <div class="cta-button" @click="openURL(getCTAObject(items).link)">{{ getCTAObject(items).button }}</div>
      </div>
  </div>
  
  <div v-else-if="mode === 'square'" class="grid-container">
    <div v-for="item in JSON.parse(items)" class="grid-item">
      <img v-if="item.type === 'image'" v-bind:src="item.src" @click="openURL(item.link)"/>
      <div v-else-if="item.type === 'cta'" class="cta-div">
        <h1 class="cta-title">{{ item.title }}</h1>
        <div class="cta-button" @click="openURL(item.link)">{{ item.button }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>

h1 {
  font-size: 24px;
}
.grid-container {
  width: 100%;
  max-width: 1200px;
  display: grid;
  place-content: center;
  margin: 0 auto;
  padding-bottom: 30px;
}
.grid-item {
  width: 100%;
  max-width: 400px;
  object-fit: cover;
  margin: 0;
}
img {
  height: 100%;
  width: 100%;
  max-width: 400px;
  margin: 0;
  padding: 0;
}
.cta-div {
  width: 100%;
  max-width: 400px;
  text-align: center;
  padding: 25% 0;
  margin: 0;
}
.cta-button {
  width: 40%;
  min-width: 100px;
  margin: auto;
  border: 2px solid black;
}
.rectangle {
  display: grid;
  margin: 0 auto;
  place-content: center;
}

@media (min-width: 700px) {
.grid-container {
  grid-template-columns: 33% 33% 33%;
}

.rectangle {
  background-image: v-bind("getImageObject(items, 'rectangle')");
}

.rectangle img {
  display: none;
}
}
</style>