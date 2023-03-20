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
        <tr>
          <th scope="row">
            {{ todo.id }}
          </th>
          <td>{{ todo.title }}</td>
          <td>{{ todo.userId }}</td>
          <td>{{ todo.completed }}</td>
        </tr>
      </tbody>
    </table>
    <NuxtLink to="/"> go back </NuxtLink>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: {},
    };
  },
  created() {
    this.getTodoById();
  },
  methods: {
    async getTodoById() {
      const response = await fetch(
        `https://jsonplaceholder.typicode.com/todos/${this.$route.params.todo}`
      );
      const data = await response.json();
      this.todo = data;
      console.log(data);
    },
  },
};
</script>
