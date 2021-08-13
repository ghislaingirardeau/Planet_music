<template>
  <header class="row align-items-center border p-5">

    <p class="col-2">LOGO</p>

    <nav class="col-10 text-right">
      <nuxt-link :to="{name: 'index'}" class="p-4">Deconnexion</nuxt-link>
      <label for="search">Barre de recherche</label>
      <input type="text" name="search" id="search">
      <button>Rechercher</button>
    </nav>

  </header>
</template>