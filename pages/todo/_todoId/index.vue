<template>
  <div>
    <nuxt-link :to="'/todo'">back</nuxt-link>
    <nuxt-link :to="'/todo/' + id + '/edit'">edit</nuxt-link>
    <h2>ini HALAMAN VIEW</h2>
    <h3>{{ todo.title }}</h3>
    <p>{{ todo.body }}</p>
    <p>{{ todo.userId }}</p>
  </div>
  
  
</template>

<script>
export default {
  data() {
    return {
      todo: {},
      id: this.$route.params.todoId
    }
  },
  mounted() {
    this.$axios
      .get('http://localhost:3002/todos/' + this.$route.params.todoId)
      .then((res) => {
        this.todo = res.data || {}
      })
  }
}
</script>

<style></style>
