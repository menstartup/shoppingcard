<template>
  <div>
    <v-navigation-drawer 
    v-model="drawer" 
    app
    color="blue-grey darken-4"
    >
      <ul>
          <router-link to="/home" tag="li">
          <v-icon style="color: orangered">mdi-home</v-icon>
          Home</router-link>
          <router-link to="/menu" tag="li">
          <v-icon style="color: orangered">mdi-silverware</v-icon>
          Menu</router-link>
          <router-link to="/admin" tag="li">
          <v-icon style="color: orangered">mdi-account-alert-outline</v-icon>
          Admin</router-link>
          <router-link to="/about" tag="li">
          <v-icon style="color: orangered">mdi-account-card-details-outline</v-icon>
          About</router-link>
      </ul>
    </v-navigation-drawer>
    <v-app-bar app color="orange" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Manh shopping Card</v-toolbar-title>
    </v-app-bar>
  </div>
</template>

<script>
export default {
    data: () => ({
    drawer: null
  })
};
</script>
<style style="scss" scoped>
nav ul {
    padding: 0;
    margin-top: 20px;
    text-decoration: none
}
nav li {
    color: orange;
    margin-left: 15%;
    padding: 5px 20px;
    list-style-type: none;
    cursor: pointer;
}
nav li i {
    margin-right: 10px;
}
nav li:last-child {
    position: absolute;
    bottom: 40px
}
</style>