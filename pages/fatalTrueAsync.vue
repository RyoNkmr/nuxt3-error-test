<script setup lang="ts">
const _ = await Promise.resolve(null);

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
    <h2>async: true</h2>
  </div>
</template>