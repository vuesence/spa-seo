<script setup lang="ts">
import { onMounted, ref } from "vue";
interface IOption {
  name: string
  value: string
}
const str = ref("");
onMounted(() => {
  document.querySelector('meta[property="og:description"]').content = "Home page description (og) - 1";
  document.querySelector('meta[name="twitter:description"]').content = "Home page description (tw) - 1";

  fetch("https://jsonplaceholder.typicode.com/todos/2")
      .then((response) => response.json())
      .then((json) => {
        str.value = json.title + " --- The brown mole is flying to Betelgeuse.";
        document.querySelector('meta[property="og:description"]').content = "Home page description (og) - 2";
        document.querySelector('meta[name="twitter:description"]').content = "Home page description (tw) - 2";
      });
});

const options: IOption[] = [{name: "Project name", value: "spa-seo"},{name: "Github Actions Workflow", value: "true"},{name: "Navigation drawer", value: "SimpleDrawer"},{name: "Header", value: "SimpleHeader"},{name: "Footer", value: "SimpleFooter"}];
</script>

<template>
  <div>
    <h1>{{ str }}</h1>
    <h3>Congratulations with scaffolding your vue webapp!</h3>
    <p v-if="options.length">
      Selected options:
    </p>
    <ul>
      <li
        v-for="option in options"
        :key="option.name"
      >
        {{ `${option.name}: ${option.value}` }}
      </li>
    </ul>
  </div>
</template>
