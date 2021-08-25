<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search" />
    <div v-for="name in searchComputed" :key="name">{{ name }}</div>
    {{ search }}
    {{ searchComputed }}
  </div>
</template>

<script>
import { computed, ref } from "@vue/reactivity";
export default {
  name: "Home",
  setup() {
    const search = ref("");
    const names = ref(["abc", "def", "ghi"]);

    const searchComputed = computed(() => {
      return names.value.filter((name) => name.includes(search.value));
    });
    return { names, search, searchComputed };
  },
};
</script>

<style></style>
