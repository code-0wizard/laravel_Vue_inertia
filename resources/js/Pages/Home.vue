<script setup>
</script>

<template>
  <!-- <Head :title="` | ${page.component}`" /> -->
  <Head :title="$page.component" />
  <!-- <h1>{{ $page.props.auth.user }}</h1> -->
  <Link class="mt-[600px] block" href="/" preserve-scroll>Refresh</Link>
</template>