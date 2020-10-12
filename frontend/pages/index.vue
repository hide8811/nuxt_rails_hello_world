<template>
  <div class="container">
    <input v-model="name" type="text" />
    <button @click="post">送信</button>
    <div v-for="namelist in namelists" :key="namelist.id">
      {{ namelist.name }}
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      name: "",
      namelists: [],
    };
  },
  methods: {
    post() {
      axios.post("http://localhost:3000/users", {
        name: this.name,
      });
      this.name = "";
    },
  },
  created() {
    axios.get(`http://localhost:3000/users/`).then((res) => {
      this.namelists = res.data;
    });
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  text-align: center;
}
</style>
