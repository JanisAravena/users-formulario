<template>
    <div class="container mt-5">
      <table class="table table-striped">
        <thead class="thead-light">
          <tr>
            <th scope="col">Nombre</th>
            <th scope="col">Correo Electrónico</th>
            <th scope="col">Acciones</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <td>{{ user.name }}</td>
            <td>{{ user.email }}</td>
            <td>
              <button class="btn btn-danger" @click="confirmRemoveUser(user.id)">Eliminar</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import Swal from 'sweetalert2'
  
  export default {
    computed: {
      users() {
        return this.$store.state.users
      }
    },
    methods: {
      confirmRemoveUser(userId) {
        Swal.fire({
          title: '¿Estás seguro?',
          text: "¡No podrás revertir esto!",
          icon: 'warning',
          showCancelButton: true,
          confirmButtonColor: '#3085d6',
          cancelButtonColor: '#d33',
          confirmButtonText: 'Sí, eliminarlo'
        }).then((result) => {
          if (result.isConfirmed) {
            this.removeUser(userId)
            Swal.fire(
              '¡Eliminado!',
              'El usuario ha sido eliminado.',
              'success'
            )
          }
        })
      },
      removeUser(userId) {
        this.$store.dispatch('removeUser', userId)
      }
    },
    created() {
      this.$store.dispatch('fetchUsers')
    }
  }
  </script>
  
  <style>
  </style>