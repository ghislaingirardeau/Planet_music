<template>
    <fieldset class="row m-3 border">
        <legend>{{title}} </legend>

        <div class="col-12">
            <input type="checkbox" value="pop rocks" name="musicType" v-model="musicType">
            <label for="pop rocks">pop rocks</label><br/>
        </div>
        
        <div class="col-12">
            <input type="checkbox" value="dance" name="musicType" v-model="musicType">
            <label for="dance">dance</label>
        </div>

        <div class="col-12">
            <input type="checkbox" value="latino" name="musicType" v-model="musicType">
            <label for="latino">latino</label>
        </div>

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
