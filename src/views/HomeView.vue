<script setup lang="ts">
import { onMounted, ref } from "vue";
interface IOption {
  name: string
  value: string
}
const str = ref("");
onMounted(() => {
  fetch("https://jsonplaceholder.typicode.com/todos/2")
      .then((response) => response.json())
      .then((json) => {
        str.value = json.title + " --- The brown mole is flying to Betelgeuse.";
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
