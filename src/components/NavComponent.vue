<template>
  <nav>
    <div :id="iconLogo"> /* hay que colocarlo z-index:2; */
      <button :type="button" @click="openNav">
        <img :src="require('@/assets/inguz.svg')" alt="Icon Logo" />
      </button>
    </div>
    <div class="nav-bar">
      <ul>
        <li>
          <a :href="indexView">INICIO</a>
        </li>
        <li></li>
      </ul>
    </div>
  </nav>
</template>
<style>
:root {
  --inguz_green: #99ca3b;
  --inguz_pink: #b93ec6;
}
nav {
  display: flex;
  align-items: center;
  height: 80px;
  font-size: 32px;
  font-weight: bolder;
  &:before {
    content: "";
    display: block;
    width: 2px;
    height: 60%;
    background-color: black;
    margin-right: 20px;
  }
}
button {
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 100%;
  border: solid black 6px;
  height: 80px;
  width: 80px;
  img {
    width: 50px;
    height: auto;
    background: transparent;
  }
}
button:hover {
  background: var(--inguz_pink);
}
.nav-bar {
  display: flex;
  align-items: center;
  height: 100%;
  width: 80%;
  background-color: black;
  li {
    list-style-type: none;
  }
  ul {
    display: flex;
    align-items: center;
  }
  a {
    color: white;
    text-decoration: none;
  }
}
</style>
<script setup lang="ts">
import indexView from "@/views/IndexView.vue";
</script>
