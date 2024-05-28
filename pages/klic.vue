<template>
  <div style="padding-top: 5rem;">
    <div class="klic-div">
      <img class="klic" src="/klic.svg" alt="Font">
    </div>
    <div>
      <h1 class="font-name">Nowoid.ttf</h1>
    </div>
    <div style="display: flex; justify-content: center;">
      <button class="tlacitko" type="button" @click="download()">Stáhnout font</button>
    </div>
  </div>
</template>

<script setup lang="ts">
const download = () => {
  const link = document.createElement('a')
  link.href = '/Nowoid.ttf'
  link.download = 'Nowoid.ttf'
  link.target = '_blank'
  link.click()
}
</script>

<style lang="css" scoped>
.klic-div {
  display: flex;
  justify-content: center;
  padding-bottom: 5rem;
}

.klic {
  max-width: 900px;
  width: 100%;
}

.font-name {
  font-weight: 400;
  text-align: center;
}

.tlacitko {
  display: inline-block;
  border: none;
  padding: 1rem 2rem;
  margin: 0;
  text-decoration: none;
  background: #464646;
  color: #ffffff;
  font-size: 1.2rem;
  cursor: pointer;
  transition: background 250ms ease-in-out,
    transform 150ms ease;
  -webkit-appearance: none;
  -moz-appearance: none;
  font-family: "Montserrat", sans-serif;
  border-radius: 4rem;
  font-weight: 500;
}

.tlacitko:hover {
  background: #535353;
}
</style>