<template>
  <div>
    <nuxt-link :to="'todo'">back</nuxt-link>

    create

    <form>
      <input v-model="todo.title" name="title" placeholder="judul" />
      <input
        v-model="todo.body"
        name="body"
        type="checkbox"
        placeholder="selesai"
      />
      <input v-model="todo.userId" name="userId" placeholder="usernya" />
      <button @click.prevent="kirim">kirim</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: {}
    }
  },
  methods: {
    kirim() { //FUNGSI CREATE
      this.$axios.post('http://localhost:3002/todos', this.todo).then(() => {
        this.$router.push('/todo')
      })
    }
  }
}
</script>

<style></style>
