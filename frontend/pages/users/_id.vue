<template>
  <h1>Hello, {{ name }}</h1>
</template>

<script>
export default {
  asyncData({ $axios, params }) {
    const response = $axios
      .get(`http://localhost:3000/users${params.id}`)
      .catch((err) => {
        error({
          statusCode: err.response.status,
          message: err.response.data.message,
        });
        return err.response;
      });
    console.log(response);
    return { name: response.name };
  },
};
</script>