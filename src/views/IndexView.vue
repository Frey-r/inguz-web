<template>
  <header>
    <NavComponent id="nav"></NavComponent>
  </header>
  <main>
    <section class="home-section">
      <div class="home-text">
        <span>¡Impulsa tu negocio con una web a medida hoy mismo! 🚀</span>
        <text-machine-component></text-machine-component>
      </div>
      <BannerImage class="home-image"></BannerImage>
    </section>
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
.home-section {
  display: flex;
  max-height: 100svh;
}
.home-text {
  position: absolute;
  height: 100svh;
  width: 50%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-wrap: wrap;
  gap: var(--space-m);
  flex-direction: column;
  text-align: left;
  margin-left: var(--space-15percent);
  span {
    width: 50%;
    font-size: var(--font-size-gigant);
  }
}
.home-image {
  left: 50svw;
  top: -20svh;
  position: relative;
  background-color: #11131d;
  width: 160svw;
  height: 126svh;
  border-radius: 25%;
  transform: rotate(23deg);
  z-index: -1;
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
import ServiceAccordion from "@/components/ServiceAccordion.vue";
import TextMachineComponent from "@/components/textMachineComponent.vue";
import BannerImage from "@/components/bannerImage.vue";

export default {
  name: "IndexPage",
  components: {
    TextMachineComponent,
    ServiceAccordion,
    NavComponent,
    BannerImage,
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
