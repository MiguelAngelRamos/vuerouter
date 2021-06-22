<template>
  <!-- <h1>{{ this.$route.params.id}}</h1> -->
  <div class="container mt-5 col-sm-6 offset-sm-3">
    <h1 class="text-center"> Datos del Usuario</h1>
      <table class="table">
        <thead>
          <tr>
            <th scope="col">Nombre</th>
            <th scope="col">Nick</th>
            <th scope="col">Email</th>
            <th scope="col">Dirección</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th>{{ user.name }}</th>
            <td>{{ user.username}}</td>
            <td>{{ user.email }}</td>
            <td>{{ user.address?.street}} - {{ user.address?.suite }}</td>
          </tr>
        </tbody>
      </table>
  </div>



</template>

<script>
export default {
  data() {
    return {
      user: {}
    }
  },
  methods: {
    async consumirUser() {
      try {
        const data = await fetch(`https://jsonplaceholder.typicode.com/users/${this.$route.params.id}`);
        const getUser = await data.json();
        this.user = getUser;
        console.log(this.user);
      } catch (error) {
        console.log(error);
      }
    }
  },
  created() {
    this.consumirUser()
  }

}
</script>

<style>

</style>