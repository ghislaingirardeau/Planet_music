<template>
    <fieldset>
        <legend>Vous êtes :</legend>
            <input type="radio" value="Amateur" v-model="userStatus">
            <label for="Amateur">Amateur</label>

            <input type="radio" value="professional" v-model="userStatus">
            <label for="professional">Professionnel</label>
    </fieldset>
</template>

<script>
export default {
    data() {
        return {
            userStatus: String
        }
    },
}
</script>