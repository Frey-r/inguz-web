<template>
  <div>
    <p>Inguz te ofrece</p>
    <h1 class="texto-dinamico">{{ textoActual }}</h1>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

const textoDinamico = ["Innovación", "Crecimiento", " Alcance"];
const textoActual = ref("");

onMounted(() => {
  escribirTexto(0);
});

async function escribirTexto(index) {
  const texto = textoDinamico[index];
  for (let i = 0; i < texto.length; i++) {
    textoActual.value += texto[i];
    await esperar(100); // Puedes ajustar la velocidad aquí
  }
  await esperar(1000); // Espera un segundo antes de borrar
  borrarTexto();
  await esperar(1000); // Espera un segundo antes de escribir el siguiente texto
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
</script>

<style>
.texto-dinamico {
  display: inline-block;
  white-space: nowrap;
  overflow: hidden;
  border-right: 4px solid;
  width: fit-content;
}

@keyframes typing {
  from {
    width: 0;
  }
}

@keyframes blink {
  50% {
    border-color: transparent;
  }
}

.texto-dinamico::after {
  content: "|";
  display: inline-block;
  width: 1px;
  animation: blink 0.5s infinite linear;
}
</style>
