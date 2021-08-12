<template>
    <main class="container">

        <h1 class="row">Se connecter à mon espace musique</h1>

        <form v-on:submit.prevent>

          <div>
            <label class="col-2 m-3" for="pseudo">pseudo : </label>
            <input class="col-3 m-3" type="text" name="pseudo" id="pseudo" v-model="pseudo">
          </div>

          <div>
            <label class="col-2 m-3" for="password">Votre mot de passe: </label>
            <input class="col-3 m-3" type="password" name="password" id="password" v-model="password">
          </div>

          <div class="col-12 m-3">
            <button type="submit"><nuxt-link :to="{name: 'home'}">Page Connection</nuxt-link></button>
          </div>

        </form>
  
    </main>
</template>

<script>

export default {
  layout: 'landing',
  data () {
    return {
     pseudo: "",
     password: ""

    }
  },
  computed: {
   
  },
  methods: {
        
  }
}
</script>