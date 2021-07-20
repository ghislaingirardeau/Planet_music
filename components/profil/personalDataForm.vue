<template>
    <fieldset >
        <legend>{{title}} </legend>
        <label for="name">Votre nom : </label>
        <input type="text" name="lastname" id="lastname" v-model="lastname">
        <label for="name">Votre prénom : </label>
        <input type="text" name="firstname" id="firstname" v-model="firstname">
        <label for="name">Date de naissance : </label>
        <input type="date" name="birth" id="birth" max="2021-12-31" v-model="birth">
        <label for="name">Localisation : </label>
        <input type="text" name="localisation" id="localisation" v-model="localization">
        <label for="email">Enter your email: </label>
        <input type="email" name="email" id="email" v-model="email">
    </fieldset>

    
</template>

<script>
export default {
    data () {
        return {
            lastname: "",
            firstname: "",
            birth: "",
            localization: "",
            email: "",
            index: 0
            
        }
    },
    props: {
        title: String
    },

}
</script>