<template>
  <header class="row align-items-center p-3">

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

  </header>
</template>

<style>

</style>