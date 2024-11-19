<template>
    <div class="container mt-5 d-flex justify-content-center">
      <div class="w-50">
        <h1 class="text-center">Crear Usuario</h1>
        <form @submit.prevent="addUser">
          <div class="form-group">
            <label for="name">Nombre</label>
            <input v-model="name" type="text" class="form-control" id="name" placeholder="Nombre" required />
          </div>
          <div class="form-group">
            <label for="email">Correo Electrónico</label>
            <input v-model="email" type="email" class="form-control" id="email" placeholder="Correo Electrónico" required />
          </div>
          <button type="submit" class="btn btn-primary mt-3 w-100">Agregar Usuario</button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        email: ''
      };
    },
    methods: {
      addUser() {
        const user = { name: this.name, email: this.email };
        this.$store.dispatch('addUser', user);
        this.name = '';
        this.email = '';
      }
    }
  };
  </script>
  
  <style>
  </style>