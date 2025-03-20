<script setup>
  defineProps({
    user: String
  })
</script>

<template>
  <Head title=" | About" />
  <div>
    <h1>about page {{ user }}</h1>
  </div>
</template>