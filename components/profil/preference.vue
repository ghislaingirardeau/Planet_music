<template>
    <fieldset>
        <legend>Type de formation privilégié :</legend>
            <input type="radio" value="distance" v-model="trainingPreference" @click="next">
            <label for="distance">Formation à distance</label>

            <input type="radio" value="presencial" v-model="trainingPreference" @click="next">
            <label for="presencial">Formation en présentielle</label>

    </fieldset>
</template>

<script>
export default {
    data() {
        return {
            trainingPreference: String,
        }
    },
    props: {
        next: Function
    },
}
</script>