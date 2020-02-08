<template>
  <form @submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username" />
    </div>
    <div>
      <label for="password">password: </label>
      <input id="password" type="text" v-model="password" />
    </div>
    <button type="submit">로그인</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      pasword: '',
    };
  },
  methods: {
    submitForm() {
      axios.post();
    },
  },
};
</script>

<style></style>
