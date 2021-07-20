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

        <!-- <svg viewBox="0 0 350 250">
  <path fill="none" stroke="red"
    d="M20,50 C20,-50 180,150 180,50 C180-50 20,150 20,50 z" />

  <circle r="5" fill="red">
    <animateMotion dur="10s" repeatCount="indefinite"
      path="M20,50 C20,-50 180,150 180,50 C180-50 20,150 20,50 z" />
  </circle>
</svg> -->

<button @click="reloaded">reload</button>
<svg viewBox="0 0 400 400" :key="reload">
  <path fill="none" stroke="red" 
  d="m 0 0 c 2 57 25 14 59 14
  "> </path>
  <circle r="5" fill="red" id='circle_animation'>
    <animateMotion dur="2s" repeatCount="2"
      path="m 0 0 c 2 57 25 14 59 14"/>
  </circle>
</svg>
  
    </main>
</template>

<script>

export default {
  layout: 'landing',
  data () {
    return {
      docState: "",
      test: "noir",
      reload: false,
      anim: `dur="2s" repeatCount="2" path="m 0 0 c 2 57 25 14 59 14"`
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
  },
  methods: {
        
    reloaded() {
      this.reload = !this.reload
    }
  }
}
</script>