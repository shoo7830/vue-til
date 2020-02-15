<template>
  <div class="contents">
    <div class="form-wrapper">
      <h1 class="page-header">생성 페이지</h1>
      <form class="form" @submit.prevent="submitForm">
        <div>
          <label for="title">Title: </label>
          <input type="text" id="title" v-model="title" />
        </div>
        <div>
          <label for="contents">Contnents:</label>
          <textarea type="text" id="contents" rows="5" v-model="contents" />
          <p class="validation-text warning" v-if="!isContentsValid">
            contents must be less than 200
          </p>
        </div>
        <button type="submit" class="btn">Create</button>
      </form>
      <p class="log">
        {{ logMessage }}
      </p>
    </div>
  </div>
</template>

<script>
import { createPost } from '@/api/index';
export default {
  data() {
    return {
      title: '',
      contents: '',
      logMessage: '',
    };
  },
  computed: {
    isContentsValid() {
      return this.contents.length <= 200;
    },
  },
  methods: {
    async submitForm() {
      try {
        const response = await createPost({
          title: this.title,
          contents: this.contents,
        });
        console.log(response);
      } catch (error) {
        console.log(error.response.data.message);
        this.logMessage = '동일한 게시글이 존재합니다.';
      }
    },
  },
};
</script>

<style scoped>
.form-wrapper .form {
  width: 100%;
}

.btn {
  color: #fff;
}
</style>
