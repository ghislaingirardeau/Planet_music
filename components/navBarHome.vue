<template>
  <header class="row align-items-center p-3 header__home">

    <div class="col-4">
      <div>LOGO</div>
      <div><nuxt-link :to="{name: 'index'}" class="d-block">Deconnexion</nuxt-link></div>
    </div>

    <nav class="col-8 text-right">
      <nuxt-link :to="{name: '#'}" class="p-4">Tableau de bord</nuxt-link>
      <nuxt-link :to="{name: '#'}" class="p-4">Reseau</nuxt-link>
      <nuxt-link :to="{name: '#'}" class="p-4">Messagerie</nuxt-link>
      <nuxt-link :to="{name: '#'}" class="p-4">Notification</nuxt-link>
      <nuxt-link :to="{name: '#'}" class="p-4">Profil</nuxt-link>
    </nav>

<!-- SEARCH PUBLICATION, MUSIC LESSON, CONCERT FOR FREE -->
    <div class="col-12 mt-4">
      <label for="search">Barre de recherche</label>
      <input type="text" name="search" id="search">
      <button>Rechercher</button>
    </div>

  </header>
</template>

<style>

</style>