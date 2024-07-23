<script>
//options API in Vue
export default {
  data() {
    return {
      name: "M. Asad khan",
      status: "active",
      skills: [
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
      ],
      link: "https://www.google.com",
    };
  },
  methods: {
    toggleStatus() {
      switch (this.status) {
        case "active":
          this.status = "pending";
          break;
        case "pending":
          this.status = "inactive";
          break;
        default:
          this.status = "active";
          break;
      }
    },
  },
};
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
    <ul>
      <li v-for="skill in skills" :key="skill">{{ skill }}</li>
    </ul>
  </div>

  <div>
    <h1>Link binding</h1>
    <a :href="link" target="_blank">Click for Google</a>
  </div>
</template>
