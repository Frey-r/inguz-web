<template>
  <div class="texto-dinamico-container">
    <p>Inguz te ofrece</p>
    <h1 class="texto-dinamico" :style="{ color: textColor }">{{ textoActual }}</h1>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

const textoDinamico = ["Innovación", "Crecimiento", "Alcance"];
const textoActual = ref("");
let textColor = ""; // Define textColor here

onMounted(() => {
  escribirTexto(0);
});

async function escribirTexto(index) {
  const texto = textoDinamico[index];
  txt_color(index);
  for (let i = 0; i < texto.length; i++) {
    textoActual.value += texto[i];
    await esperar(100); // Puedes ajustar la velocidad aquí
  }
  await esperar(1000); // Espera un segundo antes de borrar
  borrarTexto();
  await esperar(1500); // Espera un segundo antes de escribir el siguiente texto
  if (index < textoDinamico.length - 1) {
    escribirTexto(index + 1);
  } else {
    escribirTexto(0);
  }
}

async function borrarTexto() {
  const texto = textoActual.value;
  for (let i = texto.length - 1; i >= 0; i--) {
    textoActual.value = textoActual.value.slice(0, i);
    await esperar(100); // Puedes ajustar la velocidad aquí
  }
}

function esperar(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

function txt_color(index) {
  if (index % 2 === 0) {
    textColor = "#99ca3b"; // Assign textColor here
  } else {
    textColor = "#b93ec6"; // Assign textColor here
  }
}
</script>

<style>
.texto-dinamico-container {
  display: flex;
  font-size: var(--font-size-big);
  min-height: 2ch;
  p {
    margin-right: 1ch;
  }
}
.texto-dinamico {
  display: inline-block;
  white-space: nowrap;
  overflow: hidden;
  border-right: 4px solid;
  width: fit-content;
}
</style>
