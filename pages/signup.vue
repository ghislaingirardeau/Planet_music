<template>
    <main class="container__signup">
        <button><nuxt-link :to="{name: 'home'}">home</nuxt-link></button>

        <h1>Signup</h1>

        <button @click="prev">prev</button>
        

        <form class="form__signup" id="form">
            <!-- bloc personal data -->
            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 0">
                    <personalData :title="titleData" :next="next" />
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 1">
                    <status />
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
                <fieldset class="form__bloc" v-show="on === 3">
                    <instrumentSelect :title="titleInstrument" :next="next"/>
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 4 ">
                 <kindSelect :title="titleKind" :next="next"/>
                </fieldset>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <fieldset class="form__bloc" v-show="on === 5">
                    <preference />
                </fieldset>
            </transition>



        </form>

    </main>
</template>

<script>
import instrumentSelect from '@/components/musicSelection/instrumentSelect.vue'
import kindSelect from '@/components/musicSelection/kindSelect.vue'
import personalData from '~/components/profil/personalData.vue'
import status from '@/components/profil/status.vue'
import preference from '@/components/profil/preference.vue'

export default {
  layout: 'landing',
  data() {
        return {
            on: 0,
            userCategory: String,
            direction: '',
            titleData: "Pour mieux vous connaitre...",
            titleInstrument: "Choississez vos instruments favoris",
            titleKind: "Choississez vos styles musicals",
            index: 0
        }
    },
    components: {
        instrumentSelect,
        kindSelect,
        personalData,
        status,
        preference
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