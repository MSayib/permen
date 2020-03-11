<template>

  <div>
    <div>
  <b-jumbotron header="BootstrapVue" lead="Bootstrap v4 Components for Vue.js 2">
    <p>For more information visit website</p>
    <b-button variant="primary" href="#">More Info</b-button>
  </b-jumbotron>
</div>
    <nuxt-link :to="'/todo'">back</nuxt-link>
    <b-button variant="primary" @click="kirim">update</b-button>
    <form> 
      Title:<input v-model="todo.title" name="title" placeholder="judul" />
      Body:<input 
        v-model="todo.body"
        name="completed"
        type="text"
        placeholder="selesai"
      />
      UserId:<input v-model="todo.userId" name="userId" placeholder="usernya" />
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
  mounted() {
    this.getDetail()
  },
  methods: {
    getDetail() { // INI CODE UNTUK LIAT VIEW DETAILS
      this.$axios
        .get('http://localhost:3002/todos/' + this.$route.params.todoId)
        .then((res) => {
          this.todo = res.data || {}
        })
    },
    kirim() { // INI CODE UNTUK UPDATE (PATCH)
      this.$axios
        .patch(
          'http://localhost:3002/todos/' + this.$route.params.todoId,
          this.todo
        )
        .then(() => {
          this.$router.push('/todo')
        })
    }
  }
}
</script>

<style></style>
