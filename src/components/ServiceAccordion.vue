<template>
  <section class="services">
    <!-- Utiliza v-for para generar una tarjeta por cada servicio -->
    <div
      v-for="service in services"
      :key="service.id"
      class="service"
      :id="'service_' + service.id"
    >
      <details class="accordion-body bg-white" name="services">
        <summary class="accordion-header">
          <article class="accordion-head">
            <h1 class="accordion-title">
              {{ service.name }}
            </h1>
            <!--suppress TypeScriptUnresolvedReference -->
            <h2>
              {{ service.subtitle }}
            </h2>
          </article>
          <!--suppress TypeScriptUnresolvedReference -->
          <h3 class="accordion-price">${{ service.price }}</h3>
        </summary>
        <footer class="accordion-footer">
          <p class="accordion-info">{{ service.info }}</p>
        </footer>
      </details>
    </div>
  </section>
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
  height: 20%;
  cursor: pointer;
  .accordion-head {
    text-align: left;
    font-size: var(--font-size-big);
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
  font-size: var(--font-size-big);
}
.accordion-footer {
  p {
    color: black;
    text-align: left;
    padding: var(--space-m);
    font-size: var(--font-size-medium);
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
