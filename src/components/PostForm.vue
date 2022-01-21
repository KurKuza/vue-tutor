<template>
  <form @submit.prevent>
    <h4>Cоздание поста</h4>
    <input
      v-bind:value="post.title"
      @input="post.title = $event.target.value"
      class="input"
      type="text"
      placeholder="Название"
    />
    <input
      v-bind:value="post.body"
      @input="post.body = $event.target.value"
      class="input"
      type="text"
      placeholder="Описание"
    />
    <button class="btn">Создать</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background-color: none;
  cursor: pointer;
  color: teal;
  border: 1px solid teal;
}
input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  outline: none;
  margin-top: 10px;
}
</style>