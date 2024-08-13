<template>
  <div class="container" style="padding: 50px 0 100px 0">
    <Account v-if="user" />
    <Auth v-else />
  </div>
</template>

<script setup>
const user = useSupabaseUser()
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bulma@1.0.2/css/bulma.min.css";
</style>