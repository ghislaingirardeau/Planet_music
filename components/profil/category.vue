<template>
    <fieldset class="row m-3">
        <legend>{{title}} </legend>

        <div class="col-12">
            <input type="radio" value="student" v-model="userCategory" @click="next">
            <label for="student">Elève, je souhaite apprendre un nouvel instrument</label>
        </div>

        <div class="col-12">
            <input type="radio" value="professor" v-model="userCategory" @click="next">
            <label for="professor">Professeur, je souhaite mettre en ligne mes cours de musique</label>
        </div>

        <div class="col-12">
            <input type="radio" value="musician" v-model="userCategory" @click="next">
            <label for="musician">Musicien ou Groupe de musique</label>
        </div>

        <div class="col-12">
            <input type="radio" value="festival" v-model="userCategory" @click="next">
            <label for="festival">Festival, bar, Association, je cotoye le monde de la musique et je souhaite étendre mon
                réseau de relation
            </label>
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