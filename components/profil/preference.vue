<template>
    <fieldset>
        <legend>Type de formation privilégié :</legend>
            <input type="radio" value="distance" v-model="trainingPreference">
            <label for="distance">Formation à distance</label>

            <input type="radio" value="presencial" v-model="trainingPreference">
            <label for="presencial">Formation en présentielle</label>
    </fieldset>
</template>

<script>
export default {
    data() {
        return {
            trainingPreference: String
        }
    },
}
</script>