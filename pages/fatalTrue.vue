<script setup lang="ts">
throw createError({
  statusCode: 404,
  message: 'pageがありません(message)',
  statusMessage: 'pageがありません(statusMessage)',
  fatal: true,
})
</script>

<template>
  <div>
    <h1>fatal: true</h1>
    <h2>async: false</h2>
  </div>
</template>