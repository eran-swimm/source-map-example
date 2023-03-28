<script setup lang="ts">
import { computed, defineAsyncComponent, ref } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0);
const boo = computed(() => {
  return `boo ${count.value}`;
})

function clicked() {
  count.value++;
  if (count.value === 3) {
    method1()
  }
  if (count.value === 5) {
    method2();
  }
}

function method1() {
  console.log("In method1 before debugger");
  debugger;
  console.log("In method1 after debugger");
}

const MyComp = defineAsyncComponent(() =>
  import('./DynComp.vue')
)
const foo = ref('aaa');
const bar = computed(() => {
  return `bar ${count.value}`;
})
function method2() {
  console.log("In method2 before debugger");
  debugger;
  console.log("In method2 after debugger");
}
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="clicked">count is {{ count }}</button>
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
  <h3>{{ foo }}</h3>
  <h3> {{ bar }}</h3>
  <h3> {{  boo  }}</h3>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
