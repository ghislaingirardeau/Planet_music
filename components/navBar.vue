<template>
  <header class="row align-items-center border p-5">

    <p class="col-6">LOGO</p>
    <nav class="col-6 text-right">
      <nuxt-link :to="{name: 'index'}" class="p-4">Accueil</nuxt-link>
      <nuxt-link :to="{name: 'login'}" class="p-4">Se connecter</nuxt-link>
      <nuxt-link :to="{name: 'signup'}" class="p-4">S'inscrire</nuxt-link>

    </nav>
  </header>
</template>