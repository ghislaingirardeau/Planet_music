<template>
    <main>
        <h1>Page login</h1>
        <button><nuxt-link :to="{name: 'home'}">home</nuxt-link></button>
        <input type="text" name="" id="" v-model="docState">
        <transition>
          <button v-bind:key="docState">
            {{ buttonMessage }}
          </button>
        </transition>

        <todoButton :item="test">
          <slot></slot>
        </todoButton>  

    </main>
</template>

<script>

export default {
  layout: 'landing',
  data () {
    return {
      docState: "",
      test: "noir",
    }
  },
  computed: {
    buttonMessage: function () {
      switch (this.docState) {
        case 'saved': return 'Modifier'
        case 'edited': return 'Sauver'
        case 'editing': return 'Annuler'
      }
    },
  }
}
</script>