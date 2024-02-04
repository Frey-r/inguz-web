<template>
  <NavComponent></NavComponent>
  <div class="test-msg">
    <p>
      {{ msg }}
    </p>
  </div>
</template>

<script>
import axios from "axios";
import NavComponent from "@/components/NavComponent.vue";
export default {
  name: "IndexPage",
  components: { NavComponent },
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
}
</style>
