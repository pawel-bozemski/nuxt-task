<template>
  <div class="container">
    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Title</th>
          <th scope="col">User ID</th>
          <th scope="col">Completed</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="todo in todos">
          <th scope="row">
            <nuxt-link
              :to="`/todo/${todo.id}`"
              class="text-decoration-none text-dark link"
            >
              {{ todo.id }}
            </nuxt-link>
          </th>
          <td>
            <nuxt-link
              :to="`/todo/${todo.id}`"
              class="text-decoration-none text-dark link"
            >
              {{ todo.title }}
            </nuxt-link>
          </td>
          <td>
            <nuxt-link
              :to="`/todo/${todo.id}`"
              class="text-decoration-none text-dark link"
            >
              {{ todo.userId }}
            </nuxt-link>
          </td>
          <td>
            <nuxt-link
              :to="`/todo/${todo.id}`"
              class="text-decoration-none text-dark link"
            >
              {{ todo.completed }}
            </nuxt-link>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: "",
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/todos"
      );
      const data = await response.json();
      this.todos = data;
    },
  },
};
</script>

<style>
.link:hover {
  color: #0a58ca !important;
}
</style>
