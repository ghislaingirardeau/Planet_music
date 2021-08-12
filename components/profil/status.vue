<template>
    <fieldset class="row m-3">
        <legend>Vous êtes :</legend>

        <div class="col-12">
            <input type="radio" value="Amateur" v-model="userStatus" @click="next">
            <label for="Amateur">Amateur</label>
        </div>

        <div class="col-12">
            <input type="radio" value="professional" v-model="userStatus" @click="next">
            <label for="professional">Professionnel</label>
        </div>

    </fieldset>
</template>

<script>
export default {
    data() {
        return {
            userStatus: String,
        }
    },
    props: {
        next: Function
    },
}
</script>