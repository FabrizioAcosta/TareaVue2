<template>
  <div id="app">
    <!-- Barra de navegación con enlaces a diferentes rutas -->
    <nav class="navbar navbar-expand-lg navbar-dark" style="background-color: #007bff;">
      <div class="container-fluid">
        <!-- Enlace a la página de inicio -->
        <router-link to="/" class="navbar-brand">
          <i class="bi bi-house-door-fill"></i> Home
        </router-link>

        <!-- Menú de navegación -->
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <!-- Enlace para agregar tarea -->
              <router-link to="/addtask" class="nav-link">
                <i class="bi bi-plus-circle-fill"></i> Agregar Tarea
              </router-link>
            </li>
            <li class="nav-item">
              <!-- Enlace para lista de tareas -->
              <router-link to="/tasklist" class="nav-link">
                <i class="bi bi-list-check"></i> Lista de Tareas
              </router-link>
            </li>
            <li class="nav-item">
              <!-- Enlace para vista combinada -->
              <router-link to="/combinedview" class="nav-link">
                <i class="bi bi-layout-wtf"></i> Vista Combinada
              </router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Aquí se cargará el componente correspondiente a la ruta seleccionada -->
    <router-view />
  </div>
</template>

<style scoped>
/* Estilo para el fondo de la barra de navegación */
nav {
  background-color: #007bff !important; /* Azul claro */
}

/* Cambiar color de los íconos y texto cuando se pase el mouse */
nav a:hover {
  color: #ffffff !important;
  text-decoration: none;
}

.navbar-brand i,
.nav-link i {
  margin-right: 8px; /* Espacio entre el ícono y el texto */
}

.navbar-nav {
  display: flex;
  align-items: center;
}

.navbar-nav .nav-link {
  font-size: 16px;
  font-weight: bold;
  color: #ffffff !important; /* Color blanco para el texto */
}
</style>
