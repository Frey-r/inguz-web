<template>
  <div class="services">
    <!-- Utiliza v-for para generar una tarjeta por cada servicio -->
    <div
      v-for="service in services"
      :key="service.id"
      class="service"
      :id="'service_' + service.id"
    >
      <details
        class="accordion-body transition duration-200 ease-in-out bg-white"
        name="services"
      >
        <summary class="accordion-header">
          <h1 class="accordion-title">
            {{ service.name }} - {{ service.subtitle }}
          </h1>
          <!--suppress TypeScriptUnresolvedReference -->
          <h3 class="accordion-price">${{ service.price }}</h3>
        </summary>
        <footer class="accordion-footer">
          <p class="accordion-info">{{ service.info }}</p>
        </footer>
      </details>
      <div class="shine"></div>
    </div>
  </div>
</template>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
.services {
  width: 100%;
  justify-content: center;
}
.accordion-body {
  padding-left: var(--space-15percent);
  padding-right: var(--space-15percent);
  width: 100%;
  transition: all 0.3s ease;
}
.accordion-header {
  width: 100%;
  padding: 15px;
  display: flex;
  justify-content: space-between;
  h1 {
    text-align: left;
  }
}
.accordion-title {
  font-weight: bolder;
  color: var(--inguz_green);
}
.accordion-price {
  align-self: flex-end;
  font-weight: bold;
  color: var(--inguz_pink);
  font-size: 1.4rem;
}
.accordion-footer {
  p {
    color: black;
    text-align: left;
    padding-left: var(--space-m);
    padding-right: var(--space-m);
  }
}
</style>

<script setup lang="ts">
import axios from "axios";
import { onMounted, reactive } from "vue";

// Utiliza un objeto reactiva para almacenar los servicios
const services = reactive([]);

async function fetchData() {
  try {
    const path = "http://127.0.0.1:5000/services";
    const response = await axios.get(path);
    services.splice(0, services.length, ...response.data);
    console.log(response.data);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
}

onMounted(() => {
  fetchData();
});
</script>
