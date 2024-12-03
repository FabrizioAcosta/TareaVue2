<template>
  <div class="home text-center">
    <!-- Bienvenida y descripción de la aplicación -->
    <div class="welcome-section mb-5">
      <h1 class="mb-4 text-success">Bienvenido a la Aplicación de Tareas con Vue</h1>
      <p class="lead">
        Esta aplicación te permite gestionar tus tareas de manera eficiente. Puedes añadir nuevas tareas manualmente o extraerlas desde una API.
      </p>
    </div>

    <!-- Logo de Vue -->
    <div class="vue-logo mb-4">
      <img alt="Vue logo" src="../assets/logo.png" class="img-fluid" style="max-width: 200px;">
    </div>

    <!-- Descripción de las secciones -->
    <div class="sections">
      <h3 class="text-success">Secciones de la Aplicación</h3>
      <ul class="list-unstyled">
        <li><strong>Añadir Tarea:</strong> Permite ingresar nuevas tareas manualmente.</li>
        <li><strong>Lista de Tareas:</strong> Muestra todas las tareas extraídas desde la API, permitiendo marcarlas como completadas o eliminarlas.</li>
        <li><strong>Vista Combinada:</strong> Combina las funcionalidades de añadir tareas manualmente y ver las tareas de la API al mismo tiempo.</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
}
</script>

<style scoped>
.home {
  padding: 20px;
}

.welcome-section {
  margin-bottom: 30px;
}

.vue-logo img {
  max-width: 200px;
}

.sections ul {
  text-align: left;
  display: inline-block;
}

.sections li {
  margin-bottom: 10px;
}

.sections strong {
  color: #007bff;
}

.text-success {
  color: #28a745; /* Color verde de Bootstrap */
}
</style>
