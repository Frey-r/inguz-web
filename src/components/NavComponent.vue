<template>
  <nav>
    <div :id="iconLogo">
      <button :type="button" @click="openNav">
        <img :src="require('@/assets/inguz.svg')" alt="Icon Logo" />
      </button>
    </div>
  </nav>
</template>
<style>
:root {
  --inguz_green: #99ca3b;
  --inguz_pink: #b93ec6;
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
</style>
<script setup lang="ts"></script>
