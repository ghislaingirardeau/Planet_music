<template>
    <fieldset class="row m-3 border">

        <legend class="col-12">{{title}} </legend>
        <label class="col-2 m-3" for="pseudo">pseudo : </label>
        <input class="col-3 m-3" type="text" name="pseudo" id="pseudo" v-model="pseudo">

        <label class="col-2 m-3" for="lastname">Votre nom : </label>
        <input class="col-3 m-3" type="text" name="lastname" id="lastname" v-model="lastname">

        <label class="col-2 m-3" for="firstname">Votre prénom : </label>
        <input class="col-3 m-3" type="text" name="firstname" id="firstname" v-model="firstname">

        <label class="col-2 m-3" for="birth">Date de naissance : </label>
        <input class="col-3 m-3" type="date" name="birth" id="birth" max="2021-12-31" v-model="birth">

        <label class="col-2 m-3" for="localization">Localisation : </label>
        <input class="col-3 m-3" type="text" name="localization" id="localization" v-model="localization">
        
        <legend class="col-12 m-3">Pour suivre toute l'actu musique au plus proche de chez vous !</legend>
        <label class="col-2 m-3" for="email">Enter your email: </label>
        <input class="col-3 m-3" type="email" name="email" id="email" v-model="email">
        
        <label class="col-2 m-3" for="password">Votre mot de passe: </label>
        <input class="col-3 m-3" type="password" name="password" id="password" v-model="password">
        
        <label class="col-2 m-3" for="sexe">sexe: </label>
        <input class="col-3 m-3" type="sexe" name="sexe" id="sexe" v-model="sexe">
        <!-- prof -->
        <label class="col-2 m-3" for="diplome">diplome: </label>
        <input class="col-3 m-3" type="diplome" name="diplome" id="diplome" v-model="diplome">

        <div class="col-12">
            <button @click="next">Suivant</button>
        </div>

    </fieldset>

    
</template>

<script>
export default {
    data () {
        return {
            pseudo: "",
            lastname: "",
            firstname: "",
            birth: "",
            sexe: "",
            localization: "",
            email: "",
            password: "",

            diplome: "",
        }
    },
    props: {
        title: String,
        next: Function
    },

}
</script>