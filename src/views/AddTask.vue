<template>
    <div class="add-task-container">
        <h1>Añadir Tarea</h1>
        <div class="input-group">
            <input 
                v-model="newTask" 
                @keyup.enter="addTask" 
                placeholder="Añadir nueva tarea" 
                class="task-input"
            />
            <button @click="addTask" class="add-button">Añadir</button>
        </div>

        <div v-if="tasks.length > 0" class="task-list">
            <div v-for="task in tasks" :key="task.id" class="task-item">
                <span :class="{ completed: task.completed }">{{ task.todo }}</span>
                <div class="task-actions">
                    <!-- Botón de completar (verde) -->
                    <button @click="toggleTaskCompletion(task)" class="btn btn-complete">
                        <span>Completar</span>
                        <i class="bi bi-check-circle"></i> <!-- Ícono check-circle -->
                    </button>
                    
                    <!-- Botón de eliminar (rojo) -->
                    <button @click="deleteTask(task)" class="btn btn-delete">
                        <span>Eliminar</span>
                        <i class="bi bi-trash"></i> <!-- Ícono trash -->
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "AddTask",
    data() {
        return {
            newTask: "", // Campo de entrada para la nueva tarea
            tasks: [],   // Lista de tareas locales
        };
    },
    methods: {
        addTask() {
            if (this.newTask.trim() === "") return;

            const newTask = {
                todo: this.newTask,
                completed: false,
                id: Date.now(), 
            };

            // Añadir la nueva tarea al inicio de la lista
            this.tasks.unshift(newTask);
            this.newTask = ""; // Limpiar el campo de entrada después de agregar
        },

        // Elimina una tarea específica de la lista
        deleteTask(task) {
            this.tasks = this.tasks.filter((t) => t.id !== task.id);
        },

        // Cambia el estado de la tarea entre completada y no completada
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },
    },
};
</script>

<style scoped>
.add-task-container {
    padding: 20px;
    max-width: 400px;
    margin: 0 auto;
}

.input-group {
    display: flex;
    margin-bottom: 10px;
}

.task-input {
    flex-grow: 1;
    padding: 8px;
    margin-right: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.add-button {
    padding: 8px 12px;
    border: none;
    border-radius: 4px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
}

.task-list {
    margin-top: 20px;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #eee;
}

.task-actions {
    display: flex;
    gap: 10px;
}

button {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 5px 10px;
    border: none;
    background: transparent;
    cursor: pointer;
    font-size: 1em;
}

/* Estilo de los botones de acción */
button span {
    margin-right: 5px;  /* Espacio entre el texto y el ícono */
}

button i {
    font-size: 1.5em; /* Tamaño del ícono */
    color: inherit;   /* Los íconos heredarán el color del botón */
}

/* Botón de Completar - Verde */
.btn-complete {
    color: #28a745; /* Color verde */
    border: 1px solid #28a745; /* Borde verde */
}

.btn-complete:hover {
    background-color: #28a745;
    color: white;
}

.btn-complete i {
    color: inherit;
}

/* Botón de Eliminar - Rojo */
.btn-delete {
    color: #dc3545; /* Color rojo */
    border: 1px solid #dc3545; /* Borde rojo */
}

.btn-delete:hover {
    background-color: #dc3545;
    color: white;
}

.btn-delete i {
    color: inherit;
}

/* Estilo para el texto tachado en tareas completadas */
.completed {
    text-decoration: line-through;
    color: gray;
}

</style>
