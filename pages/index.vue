<script setup>
const { data } = await useAsyncData("count", () => $fetch("/api/count"));
</script>
<template>
  <h1>Index Page</h1>
  Page visits: {{ data }}
</template>