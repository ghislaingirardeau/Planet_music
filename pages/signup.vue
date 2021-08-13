<template>
    <main class="container main__signup">

        <h1 class="row">S'incrire</h1>
        <button @click="PostData" v-if="on === 5">Send</button>
        <button @click="prev" v-if="on > 0">Retour</button>

        <form id="signup__bloc" v-on:submit.prevent> <!-- Empecher envoie du formulaire au click du bouton suivant -->
            <transition :name="animationForm" mode="out-in">
                <div class="form__bloc container" v-show="on === 0">
                    <personalData :title="titleData" :next="next" />
                </div>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <div class="form__bloc container" v-show="on === 1">
                    <status :next="next" />
                </div>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <div class="form__bloc container" v-show="on === 2">
                    <category :title="titleCategory" :next="next" />
                </div>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <div class="form__bloc container" v-show="on === 3">
                    <instrumentSelect :title="titleInstrument" :next="next"/>
                </div>
            </transition>

            <transition :name="animationForm" mode="out-in">
                <div class="form__bloc container" v-show="on === 4">
                    <kindSelect :title="titleKind" :next="next"/>
                </div>
            </transition>

            <!-- AFFICHAGE CONDITION SI ELEVE \ PROF -->
            <transition :name="animationForm" mode="out-in">
                <div class="form__bloc container" v-show="on === 5 && (this.$children[2].userCategory === 'student' || this.$children[2].userCategory === 'professor')">
                    <preference :next="next"/>
                </div>
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
import category from '@/components/profil/category.vue'

export default {
  layout: 'landing',
  data() {
        return {
            on: 0,
            direction: '',
            titleCategory: "Parlons musique, dans quelle catégorie vous situez vous :",
            titleData: "Pour mieux vous connaitre...",
            titleInstrument: "Choississez vos instruments favoris",
            titleKind: "Votre style de musique",
        }
    },
    components: {
        instrumentSelect,
        kindSelect,
        personalData,
        status,
        preference,
        category
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
        PostData() {           

            class User {
                constructor(id, status, category, instrument, musicType) {
                this.id = id
                this.status = status;
                this.category = category;
                this.instrument = instrument;
                this.musicType = musicType;
                }
            }

            let newUser = new User (
                this.$children[0].dataPost, 
                this.$children[1].userStatus, 
                this.$children[2].userCategory,
                this.$children[3].instrumentSelection, 
                this.$children[4].musicType
                )

            console.log(JSON.stringify(newUser))
        }
    }
}
</script>

<style>

</style>