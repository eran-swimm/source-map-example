<script setup lang="ts">
import { computed, defineAsyncComponent, ref } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0);

function method1() {
  console.log("In method1 before debugger");
  debugger;
  console.log("In method1 after debugger");
}

const MyComp = defineAsyncComponent(() =>
  import('./DynComp.vue')
)
function method2() {
  console.log("In method2 before debugger");
  debugger;
  console.log("In method2 after debugger");
}
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <br/>
    <button type="button" @click="method1">call method 1 - defined before</button>
    <br/>
    <button type="button" @click="method2">call method 2 - defined after</button>
    
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
    <MyComp />
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
