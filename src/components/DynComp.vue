<script setup lang="ts">
    import { computed } from 'vue';
    const content = computed(() => {
        return 'Content of dynamic';
    });
</script>

<template>
  <h1>{{  content }}</h1>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
