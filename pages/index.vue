
<script setup lang="ts">
</script>

<template>
  <div>
    <ul :class="$style.list">
      <li>
        <NuxtLink to="/fatalFalse">fatalFalse</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/fatalFalseAsync">fatalFalseAsync</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/fatalTrue">fatalTrue</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/fatalTrueAsync">fatalTrueAsync</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" module>
.list {
  li {
    margin-top: 20px;
  }
}
</style>