<script setup>
//composition API in Vue
import { ref, onMounted } from "vue";

const name = ref("M. Asad khan");
const status = ref("active");
const skills = ref([
  "Html",
  "Css",
  "Bootstrap",
  "javascript",
  "React js",
  "Node js",
  "Express js",
  "Nest js",
  "Postgresql",
  "Angular js",
  "Tailwind CSS",
]);
const link = ref("https://www.google.com");
const newTask = ref("");

const toggleStatus = () => {
  switch (status.value) {
    case "active":
      status.value = "pending";
      break;
    case "pending":
      status.value = "inactive";
      break;
    default:
      status.value = "active";
      break;
  }
};

const addTask = () => {
  if (newTask.value.trim() != "") {
    skills.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  skills.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    console.log("Todos data :-", data);
    skills.value = data.map((item) => item.title);
  } catch (error) {
    console.log("Error fetching data", error);
  }
});
</script>

<template>
  <h1>Hello Mr.{{ name }}</h1>
  <div>
    <h1>v-if v-else-if v-else binding</h1>
    <p v-if="status === 'active'">User is active</p>
    <p v-else-if="status === 'pending'">User is pending</p>
    <p v-else>User is inactive</p>
    <button @click="toggleStatus">Toggle Status to</button>
  </div>
  <div>
    <h1>v-for loop binding</h1>
    <form @submit.prevent="addTask">
      <label for="newTask">Task Title</label>
      <input type="text" id="newTask" name="newTask" v-model="newTask" />
      <button type="submit">Add Task</button>
    </form>
    <ul>
      <li v-for="(skill, index) in skills" :key="index">
        <span>{{ skill }}</span>
        <button @click="deleteTask(index)">X</button>
      </li>
    </ul>
  </div>

  <div>
    <h1>Link binding</h1>
    <a :href="link" target="_blank">Click for Google</a>
  </div>
</template>
