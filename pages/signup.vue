<template>
    <main class="container__signup">
        <button><nuxt-link :to="{name: 'home'}">home</nuxt-link></button>

        <h1>Signup</h1>

        <button @click="prev">prev</button>
        <button @click="next">next</button>

        <form class="form__signup" id="form">

            <transition :name="animationForm" mode="out-in">
                <personalDataForm :on="on" />
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form-example" v-show="on === 1">
                    <legend>Parlons musique, vous êtes :</legend>
                    <input type="radio" value="Amateur" v-model="userStatus" @click="next">
                    <label for="Amateur">Amateur</label>
                    <input type="radio" value="professional" v-model="userStatus" @click="next">
                    <label for="professional">Professionnel</label>
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form-example" v-show="on === 2">
                    <legend>Parlons musique, dans quelle catégorie vous situez vous :</legend>
                    <input type="radio" value="student" v-model="userCategory">
                    <label for="Student">Elève</label>
                    <input type="radio" value="professor" v-model="userCategory">
                    <label for="professor">Professeur</label>
                    <input type="radio" value="musician" v-model="userCategory">
                    <label for="musician">Musicien, Groupe de musique</label>
                    <input type="radio" value="festival" v-model="userCategory">
                    <label for="festival">Festival, bar, Association</label>
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form-example" v-show="on === 3 && (userCategory === 'student' || this.userCategory === 'professor')">
                    <legend>Parlons musique, choisissez votre instrument suivant sa catégorie :</legend>
                    <instrumentSelect/>
                    

                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form-example" v-show="on === 3 && (userCategory === 'musician' || this.userCategory === 'festival')">
                 <legend>Parlons musique, votre genre de musique :</legend>
                 <input type="checkbox" value="classique" name="musicType" v-model="musicType">
                 <label for="kraken">classique</label><br/>
                 <input type="checkbox" value="rocks" name="musicType" v-model="musicType">
                 <label for="sasquatch">pop rocks</label><br/>
                 <input type="checkbox" value="dance" name="musicType" v-model="musicType">
                 <label for="mothman">dance</label>
                </fieldset>
            </transition>

        </form>

    </main>
</template>

<script>
import instrumentSelect from '@/components/instruments/instrumentSelect.vue'
import personalDataForm from '@/components/profil/personalDataForm.vue'

export default {
  layout: 'landing',
  data() {
        return {
            on: 0,
            userStatus: "",
            userCategory: "",
            musicType: [],
            direction: '',
        }
    },
    components: {
        instrumentSelect,
        personalDataForm
    },
    computed: {
        animationForm() {
            return 'signup-slide-' + this.direction
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
        },
        
    }
}
</script>

<style>

</style>