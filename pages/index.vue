<template>
  <div class="main">
    <div class="ocicko-div">
      <img class="ocicko" src="/ocicko.gif" alt="Očíčko">
    </div>
    <div class="content">
      <div class="typewriter">
        <p class="text">{{ displayedText }}</p>
      </div>
      <div v-if="showButton" class="tlacitka fade-in-button">
        <div>
          <NuxtLink to="https://jakubceza.cz">
            <button class="tlacitko" type="button">Ne</button>
          </NuxtLink>
        </div>
        <div>
          <NuxtLink to="/klic">
            <button class="tlacitko" type="button">Ano</button>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const fullText = "Jsi připraven/a odhalit tajemství hlubin vesmíru?";
const displayedText = ref('');
const index = ref(0);
const speed = 100;
const showButton = ref(false);

const typeWriter = () => {
  if (index.value < fullText.length) {
    displayedText.value += fullText.charAt(index.value);
    index.value++;
    setTimeout(typeWriter, speed);
  } else {
    showButton.value = true;
  }
};

onMounted(() => {
  typeWriter();
});
</script>

<style lang="css" scoped>
.ocicko-div {
  display: flex;
  justify-content: center;
}

.ocicko {
  max-width: 350px;
  width: 100%;
}

.text {
  font-weight: 350;
  font-size: 2rem;
  text-align: center;
}

.tlacitka {
  display: flex;
  justify-content: center;
  gap: 1rem;
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

.content {
  padding-top: 1rem;
}

.main {
  padding-top: 5rem;
}

.typewriter {
  display: flex;
  justify-content: center;
  padding-bottom: 2rem;
}

.typewriter .text {
  display: inline-block;
  overflow: hidden;
  border-right: 0.15em solid #000000;
  white-space: nowrap;
  margin: 0 auto;
  text-align: center;
  letter-spacing: 0.15em;
  animation: blink-caret 0.75s step-end infinite;
}

@keyframes blink-caret {

  from,
  to {
    border-color: transparent;
  }

  50% {
    border-color: white;
  }
}

.fade-in-button {
  margin-top: 20px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  opacity: 0;
  animation: fadeIn 2s forwards;
}

@keyframes fadeIn {
  to {
    opacity: 1;
  }
}
</style>