<template>
  <div>
    <!-- navbar  -->

    <b-navbar
      toggleable="lg"
      class="bg-light-yellow py-4"
      :class="{ 'fixed-top': login == false }"
    >
      <b-container>
        <b-navbar-brand to="/" class="text-purple h2">
          Newton
        </b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto">
            <b-navbar-nav>
              <b-nav-item to="/">Home</b-nav-item>
              <b-nav-item to="/about">About Us</b-nav-item>
              <div v-if="login == false || typeof login == 'undefined'">
                <router-link to="/login" tag="b-nav-item">Login</router-link>
              </div>
              <div v-if="login && status == 'siswa'">
                <router-link to="/student" tag="b-nav-item">LMS</router-link>
              </div>
              <div v-if="login">
                <button class="btn btn-purple text-white" @click="logout()">
                  Log out
                </button>
              </div>
            </b-navbar-nav>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>
    <!-- end navbar  -->
  </div>
</template>

<script>
export default {
  props: ["login", "status"],
  methods: {
    logout() {
      localStorage.removeItem("school-website-login");
      location.reload();
    },
  },
};
</script>

<style></style>
