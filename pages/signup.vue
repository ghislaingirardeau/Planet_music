<template>
    <main>
        <button><nuxt-link :to="{name: 'home'}">home</nuxt-link></button>

        <h1>Signup</h1>

        <form action="" method="get">

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form-example" v-show="on === 0">
                    <legend>Pour mieux vous connaitre...</legend>
                    <label for="name">Votre nom : </label>
                    <input type="text" name="lastname" id="lastname" v-model="lastname" required>
                    <label for="name">Votre prénom : </label>
                    <input type="text" name="firstname" id="firstname" v-model="firstname" required>
                    <label for="name">Date de naissance : </label>
                    <input type="date" name="birth" id="birth" max="2021-12-31" v-model="birth" required>
                    <label for="name">Localisation : </label>
                    <input type="text" name="localisation" id="localisation" v-model="localization" required>
                    <label for="email">Enter your email: </label>
                    <input type="email" name="email" id="email" v-model="email" required>
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
            <fieldset class="form-example" v-show="on === 1">
                <legend>Parlons musique, vous êtes :</legend>
                <input type="radio" value="Amateur" v-model="userStatus">
                <label for="Amateur">Amateur</label>
                <input type="radio" value="professional" v-model="userStatus">
                <label for="professional">Professionnel</label>
            </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
            <fieldset class="form-example" v-show="on === 2">
                <legend>Parlons musique, dans quelle catégorie vous situez vous :</legend>
                <input type="radio" value="Student" v-model="userCategory" @click="next">
                <label for="Student">Elève</label>
                <input type="radio" value="professor" v-model="userCategory" @click="next">
                <label for="professor">Professeur</label>
                <input type="radio" value="musician" v-model="userCategory" @click="next">
                <label for="musician">Musicien, Groupe de musique</label>
                <input type="radio" value="festival" v-model="userCategory" @click="next">
                <label for="festival">Festival, bar, Association</label>
            </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
            <fieldset class="form-example" v-show="on === 3">
             <legend>Parlons musique, votre genre de musique :</legend>
             <input type="checkbox" value="classique" name="musicType" v-model="musicType">
             <label for="kraken">classique</label><br/>
             <input type="checkbox" value="rocks" name="musicType" v-model="musicType">
             <label for="sasquatch">pop rocks</label><br/>
             <input type="checkbox" value="dance" name="musicType" v-model="musicType">
             <label for="mothman">dance</label>
            </fieldset>
            </transition>

            <div>
              <input type="submit" value="Subscribe!">
            </div>
        </form>

        {{musicType}}

        <button @click="prev">prev</button>
        <button @click="next">next</button>

    </main>
</template>

<script>
export default {
  layout: 'landing',
  data() {
        return {
            on: 0,
            lastname: "",
            firstname: "",
            birth: "",
            localization: "",
            email: "",
            userStatus: "",
            userCategory: "",
            musicType: [],
            direction: '',
        }
    },
    computed: {
        animationForm() {
            return 'slide-' + this.direction
        }
    },
    methods: {
        next() {
            let formLength = document.getElementsByClassName('form-example')

            if(this.on === (formLength.length - 1)) {
                this.on
            } else {
                this.on++
                this.direction = "right"
            }
        },
        prev() {
            if(this.on === 0) {
                this.on
            } else {
                this.on--
                this.direction = "left"
            }

        }
    }
}
</script>

<style>
.slide-right-enter-active, .slide-right-leave-active {
  transition: opacity 1s;
  transform: translateX(0px);
}
.slide-right-enter, .slide-right-leave-to {
  opacity: 0;
  transform: translateX(50px);
}

.slide-left-enter-active, .slide-left-leave-active {
  transition: opacity 1s;
  transform: translateX(0px);
}
.slide-left-enter, .slide-left-leave-to {
  opacity: 0;
  transform: translateX(-50px);
}
</style>