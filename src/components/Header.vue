<template>
  <b-navbar toggleable="lg">
    <b-navbar-brand to="/"
      ><img style="padding-bottom: 20px;
padding-left: 20px;"
        height="60px" 
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b8/TUI-Travel-Logo.svg/426px-TUI-Travel-Logo.svg.png"
    /></b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" style="color: #ffffff" is-nav>
      <b-navbar-nav>
        <b-nav-item to="/Search"><img height="30px" src="https://cdn.icon-icons.com/icons2/488/PNG/512/search_47686.png"><img/></b-nav-item>
        <b-nav-item to="/">ACCUEIL</b-nav-item>
        <b-nav-item to="/Destination">DESTINATIONS</b-nav-item>
        <b-nav-item to="/Agence">L'AGENCE</b-nav-item>
        <b-nav-item to="/Contact">CONTACT</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto" style="margin-left: auto !important">
        <b-button v-if="!onlogin()" to="/Register">Register</b-button>
        <b-button v-if="!onlogin()" to="/Login">Login</b-button>
        <b-nav-item-dropdown v-if="onlogin()" right>
          <!-- Using 'button-content' slot -->
          <template  #button-content>
            <em v-if="onlogin()">ADMIN</em>
          </template>
          <b-dropdown-item to="/Poster">Ajouter une ville</b-dropdown-item>
          <b-dropdown-item to="/List">Listes villes</b-dropdown-item>
          <b-dropdown-item @click="RemoveToken()" >Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>

        <b-nav-form style="display:none">
          <b-form-input
            size="sm"
            class="mr-sm-2"
            placeholder="Search"
          ></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit"
            >Search</b-button
          >
        </b-nav-form>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      showSearch: false,
      showLogin: false,
    };
  },
  methods: {
    onclickSearch() {
      this.showSearch = !this.showSearch;
    },
    RemoveToken() {
      localStorage.removeItem("token");
    },
    onlogin() {
      const token = localStorage.getItem("token");
      return !!token;
      //return !!token;
    },
  },
};
</script>

<style>
#textboja {
  color: black !important;
  font-size: 16px;
}
</style>
