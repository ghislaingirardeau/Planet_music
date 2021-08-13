<template>
  <header class="row align-items-center p-3">

    <div class="col-4">
      <p>LOGO</p>
    </div>

    <nav class="col-6 text-right">
      <nuxt-link :to="{name: 'index'}" class="p-4">Accueil</nuxt-link>
      <nuxt-link :to="{name: 'login'}" class="p-4">Se connecter</nuxt-link>
      <nuxt-link :to="{name: 'signup'}" class="p-4">S'inscrire</nuxt-link>
    </nav>

    <nav class="col-2">
      <b-dropdown class="mx-1" left text="menu">
        <b-link class="d-block p-3" href="#concept">concept</b-link>
        <b-link class="d-block p-3" href="#vision">vision</b-link>
        <b-link class="d-block p-3" href="#offre">offre</b-link>
      </b-dropdown> 
    </nav>

    <div class="col-12 mt-4">
      <label for="search">Barre de recherche</label>
      <input type="text" name="search" id="search">
      <button>Rechercher</button>
    </div>

  </header>

</template>