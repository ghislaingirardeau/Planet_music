<template>
    <fieldset class="row m-3">
        <legend>Type de formation privilégié :</legend>

        <div class="col-12">
            <input type="radio" value="distance" v-model="trainingPreference" @click="next">
            <label for="distance">Formation à distance</label>
        </div>

        <div class="col-12">
            <input type="radio" value="presencial" v-model="trainingPreference" @click="next">
            <label for="presencial">Formation en présentielle</label>
        </div>

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