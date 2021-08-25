<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search" />
    <div v-for="name in searchComputed" :key="name">{{ name }}</div>
    {{ search }}
    {{ searchComputed }}
    <button @click="handleClick">Stop Watch and Watch Effect</button>
  </div>
</template>

<script>
import { computed, ref } from "@vue/reactivity";
import { watch, watchEffect } from "@vue/runtime-core";
export default {
  name: "Home",
  setup() {
    const search = ref("");
    const names = ref(["abc", "def", "ghi"]);

    // WATCH
    const stopWatch = watch(search, () => {
      console.log("watch");
    });

    // WATCHEFFECT
    const stopWatchEffect = watchEffect(() => {
      console.log("WatchEffect"), search.value;
    });

    const handleClick = () => {
      stopWatch();
      stopWatchEffect();
    };

    const searchComputed = computed(() => {
      return names.value.filter((name) => name.includes(search.value));
    });
    return { names, search, searchComputed, handleClick };
  },
};
</script>

<style></style>
