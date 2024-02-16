<template>
  <header>
    <NavComponent id="nav"></NavComponent>
  </header>
  <main>
    <div class="home-frame">
      <span>¡Impulsa tu negocio con una web a medida hoy mismo! 🚀</span>
      <text-machine-component></text-machine-component>
    </div>
    <BannerComponent id="BannerComponent"></BannerComponent>
    <ServiceAccordion class="service-section"></ServiceAccordion>
  </main>
  <footer></footer>
</template>

<style>
body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}
#nav {
  position: fixed;
  top: 50px;
  left: 50px;
  width: 100%;
}
#BannerComponent {
  display: none;
}
.home-frame {
  height: 100svh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: var(--space-m);
  flex-direction: column;
  span {
    width: 50%;
    font-size: var(--font-size-gigant);
  }
}
.service-section {
  display: flex;
  flex-direction: column;
  gap: var(--space-xxl);
}
</style>

<script>
import axios from "axios";
import NavComponent from "@/components/NavComponent.vue";
import BannerComponent from "@/components/BannerComponent.vue";
import ServiceAccordion from "@/components/ServiceAccordion.vue";
import TextMachineComponent from "@/components/textMachineComponent.vue";
export default {
  name: "IndexPage",
  components: {
    TextMachineComponent,
    ServiceAccordion,
    BannerComponent,
    NavComponent,
  },
  data() {
    return { msg: "pass" };
  },
  methods: {
    getResponse() {
      const path = "http://localhost:5000/index";
      axios
        .get(path)
        .then((res) => {
          console.log(res.data);
          this.msg = res.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  created() {
    this.getResponse();
  },
};
</script>
