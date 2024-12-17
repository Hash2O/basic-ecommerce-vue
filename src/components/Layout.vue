<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <div class="bg-white">
      <Navbar />
    </div>
    <slot></slot>
  </div>
</template>

<script setup>
import Navbar from './Navbar.vue'
</script>
