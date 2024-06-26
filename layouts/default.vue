<template>
  <div>
    <header class="shadow bg-white">
      <nav class="container mx-auto p-4 flex justify-between items-center">
        <div class="font-bold text-xl">Statista</div>
        <ul class="flex gap-4">
          <li><NuxtLink to="/" class="font-bold" activeClass="text-green-500">Home</NuxtLink></li>
          <li><NuxtLink to="/about" class="font-bold" activeClass="text-green-500">About</NuxtLink></li>
          <li><NuxtLink to="/contact" class="font-bold" activeClass="text-green-500">Contact</NuxtLink></li>
        </ul>
      </nav>
    </header>

    <div class="container mx-auto p-4">
      <slot />
    </div>
    
    <footer class="container mx-auto p-4 flex justify-center border-t-2 md:fixed bottom-0">
      <ul class="flex gap-4">
        <li><NuxtLink to="/" activeClass="text-green-500">Home</NuxtLink></li>
        <li><NuxtLink to="/about" activeClass="text-green-500">About</NuxtLink></li>
        <li><NuxtLink to="/imprint" activeClass="text-green-500">Imprint</NuxtLink></li>
      </ul>
    </footer>
  </div>
</template>

<script setup>

</script>

<style scoped>
  .header {
    opacity: 1;
  }
</style>
