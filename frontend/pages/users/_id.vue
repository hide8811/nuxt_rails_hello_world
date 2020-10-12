<template>
  <div>
    <h1>Hello,{{ name }}</h1>
    {{ $route.params.id }}
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      name: "",
    };
  },
  created(params) {
    axios.get(`http://localhost:3000/users/3`).then((res) => {
      this.name = res.data.name;
    });
  },
  // asyncData({ $axios, params }) {
  //   const response = $axios
  //     .get(`http://localhost:3000/users/${params.id}`)
  //     .catch((err) => {
  //       error({
  //         statusCode: err.response.status,
  //         message: err.response.data.message,
  //       });
  //       return err.response;
  //     });

  //   console.log(response.data);
  //   // return { name: response.data };
  // },
};
</script>