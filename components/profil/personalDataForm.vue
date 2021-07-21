<template>
    <fieldset >
        <legend>{{title}} </legend>
        <label for="pseudo">pseudo : </label>
        <input type="text" name="pseudo" id="pseudo" v-model="lastname">

        <label for="lastname">Votre nom : </label>
        <input type="text" name="lastname" id="lastname" v-model="lastname">

        <label for="firstname">Votre prénom : </label>
        <input type="text" name="firstname" id="firstname" v-model="firstname">

        <label for="birth">Date de naissance : </label>
        <input type="date" name="birth" id="birth" max="2021-12-31" v-model="birth">

        <label for="localization">Localisation : </label>
        <input type="text" name="localization" id="localization" v-model="localization">
        
        <p>pour suivre toute l'actu musique au plus proche de chez vous !</p>
        <label for="email">Enter your email: </label>
        <input type="email" name="email" id="email" v-model="email">
        
        <label for="password">Enter your password: </label>
        <input type="password" name="password" id="password" v-model="password">
        
        <label for="sexe">sexe: </label>
        <input type="sexe" name="sexe" id="sexe" v-model="sexe">
        <!-- prof -->
        <label for="diplome">diplome: </label>
        <input type="diplome" name="diplome" id="diplome" v-model="diplome">

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
            index: 0
            
        }
    },
    props: {
        title: String
    },

}
</script>