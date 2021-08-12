<template>
    <fieldset class="row m-3">
        <legend>{{title}} </legend>

        <div class="col-12 m-3">
            <input class="col-5" type="text" v-model="searchInst" placeholder="Rechercher un instrument" v-on:keyup.enter="searchInstrument()">
            <button type="button" id='select' @click="searchInstrument()">Search</button>
            <div v-if="showInstrument == true">
                <input type="checkbox" :value="resultSearch" name="instrumentSelection" v-model="instrumentSelection">
                <label :for="resultSearch">{{resultSearch}}</label>
            </div> 
        
            <p v-else-if="showInstrument == false">"Cet instrument n'est pas dans la liste"</p>
        </div>

        <div v-for="(item, name) in instrumentClass" :key="name">  
            <b-button v-b-modal="'my-modal'" @click="showInstruments(name, item)">{{name}}</b-button>
        </div>

        <b-modal id="my-modal" title="Sélectionner votre instrument">
            <div v-if="instrumentCategory">
                <div v-for="item in instrumentsList" :key="item">
                    <input type="checkbox" :value="item" name="instrumentSelection" v-model="instrumentSelection">
                    <label :for="item">{{item}} </label>
                </div>
            </div>
        </b-modal>

        <button @click="next">Suivant</button>

    </fieldset>

</template>

<script>
import instrument from '@/store/instruments'

export default {
    data() {
        return {
            searchInst: "",
            resultSearch: String,
            showInstrument: Boolean,
            instrumentClass: instrument,
            instrumentCategory: "",
            instrumentSelection: [],
            instrumentsList: [],
        }
    },
    computed: {
        
    },
    methods: {
        searchInstrument() {
          const textSearch = this.searchInst.toLowerCase()  
          for (let i in this.instrumentClass) {
              if(this.instrumentClass[i].find(element => element === textSearch)) {
                 this.resultSearch = this.instrumentClass[i].find(element => element === textSearch)
                 return this.showInstrument = true
              } else {
                  this.showInstrument = false
              }
            }
        },
        showInstruments(type, i) {
            this.instrumentsList = i
            return this.instrumentCategory = type
        },
    },
    props: {
        title: String,
        next: Function
    },
}
</script>
