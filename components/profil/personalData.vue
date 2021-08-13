<template>
    <fieldset class="row m-3">

        <legend class="col-12">{{title}} </legend> 
        <label class="col-2 m-3" for="pseudo">pseudo : </label>
        <input class="col-3 m-3" type="text" name="pseudo" id="pseudo" v-model="dataPost.pseudo">
        
        <label class="col-2 m-3" for="gender">Genre </label>
        <select class="col-3 m-3" name="gender" id="gender" v-model="dataPost.gender">
            <option value="M">Mr</option>
            <option value="F">Mme</option>
        </select>      
        
        <label class="col-2 m-3" for="lastname">Votre nom : </label>
        <input class="col-3 m-3" type="text" name="lastname" id="lastname" v-model="dataPost.lastname">

        <label class="col-2 m-3" for="firstname">Votre prénom : </label>
        <input class="col-3 m-3" type="text" name="firstname" id="firstname" v-model="dataPost.firstname">

        <label class="col-2 m-3" for="birth">Date de naissance : </label>
        <input class="col-3 m-3" type="date" name="birth" id="birth" max="2021-12-31" v-model="dataPost.birth">

        <label class="col-2 m-3" for="localization">Localisation : </label>
        <input class="col-3 m-3" type="text" name="localization" id="localization" v-model="dataPost.localization">
        
        <label class="col-2 m-3" for="email">Enter your email: </label>
        <input class="col-3 m-3" type="email" name="email" id="email" v-model="dataPost.email">
        
        <label class="col-2 m-3" for="password">Votre mot de passe: </label>
        <input class="col-3 m-3" type="password" name="password" id="password" v-model="dataPost.password">
        
        <label class="col-2 m-3" for="diplome">diplome: </label>
        <input class="col-3 m-3" type="diplome" name="diplome" id="diplome" v-model="dataPost.diplome">

        <div class="col-12">
            <button @click="next">Suivant</button>
        </div>

    </fieldset>

    
</template>

<script>
export default {
    data () {
        return {
            dataPost: {
                pseudo: "",
                lastname: "",
                firstname: "",
                birth: "",
                gender: "",
                localization: "",
                email: "",
                password: "",
                diplome: "",
            }
        }
    },
    props: {
        title: String,
        next: Function
    },

}
</script>