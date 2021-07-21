<template>
    <fieldset>
        <legend>{{title}} </legend>

        <input type="checkbox" value="classique" name="musicType" v-model="musicType">
        <label for="kraken">classique</label><br/>
        <input type="checkbox" value="rocks" name="musicType" v-model="musicType">
        <label for="sasquatch">pop rocks</label><br/>
        <input type="checkbox" value="dance" name="musicType" v-model="musicType">
        <label for="mothman">dance</label>

        <input type="button" value="next" @click="next">     

    </fieldset>
</template>

<script>

export default {
    data() {
        return {
            musicType: [],
        }
    },
    computed: {
        
    },
    props: {
        title: String,
        next: Function
    },
}
</script>
