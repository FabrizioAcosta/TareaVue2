<template>
  <div class="container mt-4">
    <h1 class="text-center mb-4">Lista de Tareas</h1>

    <!-- Contenedor para centrar el botón -->
    <div class="d-flex justify-content-center mb-4">
      <button @click="fetchTasks" class="btn btn-info">Cargar Tareas</button>
    </div>

    <div v-if="tasks.length > 0" class="list-group">
      <div v-for="task in tasks" :key="task.id" class="list-group-item d-flex justify-content-between align-items-center">
        <h5 :style="{ textDecoration: task.completed ? 'line-through' : 'none' }">{{ task.todo }}</h5>
        <span>{{ task.completed ? 'Completada' : 'Pendiente' }}</span>
        <div>
          <!-- Botón de completar con ícono de tilde -->
          <button @click="toggleTaskCompletion(task)" class="btn btn-sm btn-success">
            <i class="bi bi-check"></i> <!-- Ícono de tilde -->
          </button>
          <!-- Botón de eliminar con ícono de basurero -->
          <button @click="deleteTask(task)" class="btn btn-sm btn-danger">
            <i class="bi bi-trash"></i> <!-- Ícono de basurero -->
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskList",
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    async fetchTasks() {
      try {
        const response = await fetch("https://dummyjson.com/todos");
        const data = await response.json();
        this.tasks = data.todos;
      } catch (error) {
        console.error("Error al cargar las tareas:", error);
      }
    },

    toggleTaskCompletion(task) {
      task.completed = !task.completed;
    },

    deleteTask(task) {
      this.tasks = this.tasks.filter((t) => t.id !== task.id);
    },
  },
};
</script>

<style scoped>
h5 {
  margin: 5px 0;
}

button {
  margin: 5px;
}

/* Estilo adicional para los íconos */
button i {
  font-size: 1.2em;
}
</style>
