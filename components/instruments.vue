<template>
    <transition :name="animationForm" mode="out-in">
        <fieldset class="form-example">
            <legend>Choisissez vos instruments :</legend>
            <input type="checkbox" value="classique" name="instrument" v-model="instrument">
            <label for="guitare">guitare</label><br/>
            <input type="checkbox" value="rocks" name="instrument" v-model="instrument">
            <label for="batterie">batterie</label><br/>
            <input type="checkbox" value="dance" name="instrument" v-model="instrument">
            <label for="piano">piano</label>
        </fieldset>
    </transition>
</template>