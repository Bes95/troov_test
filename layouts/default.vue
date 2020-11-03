<template>
  <div>
    <nav class="navbar navbar-expand-md navbar-dark bg-dark">
      <nuxt-link to="/" class="navbar-brand">Troov test</nuxt-link>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarsExampleDefault"
        aria-controls="navbarsExampleDefault"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarsExampleDefault">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <nuxt-link to="/" class="nav-link" exact-active-class="active"
              >Accueil</nuxt-link
            >
          </li>
          <li class="nav-item">
            <nuxt-link
              to="/articles/"
              class="nav-link"
              exact-active-class="active"
              >Objets</nuxt-link
            >
          </li>
        </ul>

        <ul class="navbar-nav" v-if="!$auth.loggedIn">
          <li class="nav-item">
            <nuxt-link
              to="/user/register"
              class="nav-link"
              exact-active-class="active"
              >Inscription</nuxt-link
            >
          </li>
          <li class="nav-item">
            <nuxt-link
              to="/user/login"
              class="nav-link"
              exact-active-class="active"
              >Connexion</nuxt-link
            >
          </li>
        </ul>
        <ul class="navbar-nav" v-if="$auth.loggedIn">
          <li class="nav-item">
            <nuxt-link
              to="/user/logout"
              class="nav-link"
              exact-active-class="active"
              >Deconnexion</nuxt-link
            >
          </li>
        </ul>
      </div>
    </nav>
    <div class="container mt-4">
      <nuxt />
    </div>
  </div>
</template>
