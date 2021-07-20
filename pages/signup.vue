<template>
    <main class="container__signup">
        <button><nuxt-link :to="{name: 'home'}">home</nuxt-link></button>

        <h1>Signup</h1>

        <button @click="prev">prev</button>
        <button @click="next">next</button>


        <form class="form__signup" id="form">
            <!-- bloc personal data -->
            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 0">
                    <personalDataForm :title="titleData" />
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 1">
                    <legend>Parlons musique, vous êtes :</legend>
                    <input type="radio" value="Amateur" v-model="userStatus" @click="next">
                    <label for="Amateur">Amateur</label>
                    <input type="radio" value="professional" v-model="userStatus" @click="next">
                    <label for="professional">Professionnel</label>
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 2">
                    <legend>Parlons musique, dans quelle catégorie vous situez vous :</legend>
                    <input type="radio" value="student" v-model="userCategory" @click="next">
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
                <fieldset class="form__bloc" v-show="on === 3 && (userCategory === 'student' || this.userCategory === 'professor')">
                    <instrumentSelect :title="titleInstrument" />
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 3 && (userCategory === 'musician' || this.userCategory === 'festival')">
                 <kindSelect :title="titleKind" />
                </fieldset>
            </transition>

        </form>

    </main>
</template>

<script>
import instrumentSelect from '@/components/musicSelection/instrumentSelect.vue'
import kindSelect from '@/components/musicSelection/kindSelect.vue'
import personalDataForm from '@/components/profil/personalDataForm.vue'

export default {
  layout: 'landing',
  data() {
        return {
            on: 0,
            userStatus: "",
            userCategory: "",
            direction: '',
            titleData: "Pour mieux vous connaitre...",
            titleInstrument: "Choississez vos instruments favoris",
            titleKind: "Choississez vos styles musicals",
        }
    },
    components: {
        instrumentSelect,
        kindSelect,
        personalDataForm
    },
    computed: {
        animationForm() {
            return 'signup-slide-' + this.direction
        },
    },
    methods: {
        next() {
            let formLength = document.getElementsByClassName('form__bloc')

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