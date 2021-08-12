<template>
    <fieldset class="row m-3">
        <legend>{{title}} </legend>

        <div class="col-12">
            <input type="radio" value="student" v-model="userCategory" @click="next">
            <label for="student">Elève</label>
        </div>

        <div class="col-12">
            <input type="radio" value="professor" v-model="userCategory" @click="next">
            <label for="professor">Professeur</label>
        </div>

        <div class="col-12">
            <input type="radio" value="musician" v-model="userCategory" @click="next">
            <label for="musician">Musicien, Groupe de musique</label>
        </div>

        <div class="col-12">
            <input type="radio" value="festival" v-model="userCategory" @click="next">
            <label for="festival">Festival, bar, Association</label>
        </div>

    </fieldset>
</template>

<script>
export default {
    data() {
        return {
            userCategory: String,
        }
    },
    props: {
        title: String,
        next: Function
    },
}
</script>