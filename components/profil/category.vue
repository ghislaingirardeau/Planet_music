<template>
    <fieldset>
        <legend>{{title}} </legend>
            <input type="radio" value="student" v-model="userCategory" @click="next">
            <label for="Student">Elève</label>

            <input type="radio" value="professor" v-model="userCategory" @click="next">
            <label for="professor">Professeur</label>

            <input type="radio" value="musician" v-model="userCategory" @click="next">
            <label for="musician">Musicien, Groupe de musique</label>

            <input type="radio" value="festival" v-model="userCategory" @click="next">
            <label for="festival">Festival, bar, Association</label>
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