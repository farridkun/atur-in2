<template>
  <v-app>
    <app-navbar :user="user" :logout="logout"></app-navbar>
    <v-content>
      <router-view />
    </v-content>
    <v-footer :fixed="fixed" app>
      <v-layout column align-center>
        <span align="center" justify="center">&copy; 2020 - Made with 💙 by UHA-Developer</span>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>
import { mapActions, mapState } from "vuex";
import AppNavbar from "@/components/AppNavbar";

export default {
  name: "App",
  components: {
    AppNavbar
  },
  data() {
    return {
      fixed: false
    };
  },
  computed: {
    ...mapState("auth", { user: "payload" })
  },
  methods: {
    ...mapActions("auth", { authLogout: "logout" }),
    logout() {
      this.authLogout().then(() => this.$router.push("/login"));
    }
  }
};
</script>
