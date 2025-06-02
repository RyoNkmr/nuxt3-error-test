<script setup lang="ts">
throw createError({
  statusCode: 404,
  message: 'pageがありません(message)',
  statusMessage: 'pageがありません(statusMessage)',
  fatal: false,
})
</script>

<template>
  <div>
    <h1>fatal: false</h1>
    <h2>async: false</h2>
  </div>
</template>