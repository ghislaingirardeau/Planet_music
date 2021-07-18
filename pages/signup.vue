<template>
    <main class="container__signup">
        <button><nuxt-link :to="{name: 'home'}">home</nuxt-link></button>

        <h1>Signup</h1>

        <button @click="prev">prev</button>
        <button @click="next">next</button>

        <form action="" method="get" class="form__signup">

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

                    <button v-for="item in instrumentClass.category" :key="item" @click="showInstruments(item)">{{item}} </button>
                    
                    <transition :name="animationForm" mode="out-in">
                        <fieldset v-if="instrumentCategory === 'Corde'">
                            <div v-for="e in instrumentClass.Corde" :key="e">
                                <input type="checkbox" :value="e" name="instrumentsList" v-model="instrumentsList">
                                <label :for="e">{{e}} </label><br/>
                            </div>
                        </fieldset>
                    </transition>

                    <transition :name="animationForm" mode="out-in">
                        <fieldset v-if="instrumentCategory === 'Percussion'">
                            <div v-for="e in instrumentClass.Percussion" :key="e">
                                <input type="checkbox" :value="e" name="instrumentsList" v-model="instrumentsList">
                                <label :for="e">{{e}} </label><br/>
                            </div>
                        </fieldset>
                    </transition>

                    <transition :name="animationForm" mode="out-in">
                        <fieldset v-if="instrumentCategory === 'Clavier'">
                            <div v-for="e in instrumentClass.Clavier" :key="e">
                                <input type="checkbox" :value="e" name="instrumentsList" v-model="instrumentsList">
                                <label :for="e">{{e}} </label><br/>
                            </div>
                        </fieldset>
                    </transition>

                    <transition :name="animationForm" mode="out-in">
                        <fieldset v-if="instrumentCategory === 'Bois'">
                            <div v-for="e in instrumentClass.Bois" :key="e">
                                <input type="checkbox" :value="e" name="instrumentsList" v-model="instrumentsList">
                                <label :for="e">{{e}} </label><br/>
                            </div>
                        </fieldset>
                    </transition>

                    <transition :name="animationForm" mode="out-in">
                        <fieldset v-if="instrumentCategory === 'Cuivre'">
                            <div v-for="e in instrumentClass.Cuivre" :key="e">
                                <input type="checkbox" :value="e" name="instrumentsList" v-model="instrumentsList">
                                <label :for="e">{{e}} </label><br/>
                            </div>
                        </fieldset>
                    </transition>                        

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
import instrument from '@/store/instruments'

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
            instrumentCategory: "",
            instrumentsList: [],
            instrumentClass: instrument,
            direction: '',
            

        }
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
        showInstruments(type) {
            return this.instrumentCategory = type
        }
    }
}
</script>

<style>

</style>