<script setup>
import { computed, reactive, ref, watch } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

const user = reactive({
  name: "John Doe",
  age: 30,
});

const sentence = computed(() => {
  return `Je m'appelle ${user.name} et j'ai ${user.age} ans`;
});

// const display = () => {
//   console.log(user.name, user.age);
// };

const log = (value) => {
  console.log(value);
}

const title = ref("President");

watch(title, (newValue, oldValue) => {
  console.log(newValue, oldValue);
})
</script>

<template>
  <!-- <HelloWorld :user="user" /> -->
  <HelloWorld @updateCountry="country => log(country)">
    <!-- <template v-slot:name>{{ user.name }}</template>
    <template v-slot:age>{{ user.age }}</template> -->

  </HelloWorld>

  <span :class="{ 'text-red': user.age >= 30, 'text-green': user.age < 30 }">{{ sentence }}</span>

  <br><br>

  <input type="text" v-model="user.name" @change="display" />
  <input type="number" v-model="user.age" min="0" max="150" />

  <input type="text" v-model="title">
</template>

<style scoped>
.text-red {
  color: red;
}

.text-green {
  color: green;
}
</style>
