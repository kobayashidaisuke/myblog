<template>
  <div class="container">
    <tr v-for="task in tasks" :key="task">
      <th scope="row">{{ task.id }}</th>
      <td>{{ task.title }}</td>
      <td>{{ task.content }}</td>
      <td>{{ task.person_in_charge }}</td>
      <td>
        <router-link :to="{ name: 'task.show', params: { taskId: task.id } }">
          <button class="btn btn-primary">Show</button>
        </router-link>
      </td>
      <td>
        <router-link :to="{ name: 'task.edit', params: { taskId: task.id } }">
          <button class="btn btn-success">Edit</button>
        </router-link>
      </td>
      <td>
        <button class="btn btn-danger" @click="deleteTask(task.id)">Delete</button>
      </td>
    </tr>
  </div>
</template>


<script>
export default {
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    getTasks() {
      axios.get("/api/tasks").then((res) => {
        this.tasks = res.data;
      });
    },
    deleteTask(id) {
      axios.delete("/api/tasks/" + id).then((res) => {
        this.getTasks();
      });
    },
  },
  mounted() {
    this.getTasks();
  },
};
</script>
