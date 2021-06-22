<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Vue Router</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <!-- <a class="nav-link active" aria-current="page" href="#">Home</a> -->
          <router-link to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/users">Usuarios</router-link>
        </li>

      </ul>
    </div>
  </div>
</nav>


</template>

<script>
export default {

}
</script>

<style scoped>

.navbar-nav li {
  margin-right: 5px;
}
.navbar-nav li a {
  text-decoration: none;
  color: #524e4e;
}
.navbar {
  box-shadow: 0 0px 10px 0 rgba(0,0,0,0.4);
}

.navbar-nav li a.router-link-exact-active {
  color: rgb(12, 12, 12);
  font-weight: bold;
}

</style>