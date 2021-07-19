<template>
    <div>
        <button @click="searchInstrument()">Search</button>
        <input type="text" v-model="searchInst">
        <div v-if="showInstrument == true">
            <input type="checkbox" :value="resultSearch" name="instrumentsList" v-model="instrumentsList">
            <label :for="resultSearch">{{resultSearch}}</label>
        </div> 
        <p v-else-if="showInstrument == false">"Cet instrument n'est pas dans la liste"</p>

        <div v-for="(item, name) in instrumentClass" :key="name" >
            <button @click="showInstruments(name).prevent">{{name}} </button>
            <fieldset v-if="instrumentCategory === name">
                <div v-for="e in item" :key="e">
                    <input type="checkbox" :value="e" name="instrumentsList" v-model="instrumentsList">
                    <label :for="e">{{e}} </label>
                </div>
            </fieldset>
        </div>

    </div>
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
            instrumentsList: [],

        }
    },
    methods: {
        searchInstrument() {
          for (let i in this.instrumentClass) {
              if(this.instrumentClass[i].find(element => element === this.searchInst)) {
                 this.resultSearch = this.instrumentClass[i].find(element => element === this.searchInst)
                 return this.showInstrument = true
              } else {
                  this.showInstrument = false
              }
            }
        },
        showInstruments(type) {
            return this.instrumentCategory = type
        },
    }
}
</script>
