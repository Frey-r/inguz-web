<template>
  <NavComponent id="nav"></NavComponent>
  <BannerComponent id="BannerComponent"></BannerComponent>
</template>

<script>
import axios from "axios";
import NavComponent from "@/components/NavComponent.vue";
import BannerComponent from "@/components/BannerComponent.vue";
export default {
  name: "IndexPage",
  components: { BannerComponent, NavComponent },
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
<style>
body {
  margin: 0;
  padding: 0;
  background-color: #3a3a3a;
  overflow-x: hidden;
}
#nav {
  position: absolute;
  top: 80px;
  left: 50px;
  width: 100%;
}
#BannerComponent {
  display: none;
}
</style>
