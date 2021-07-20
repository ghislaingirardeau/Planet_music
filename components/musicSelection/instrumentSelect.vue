<template>
    <fieldset>
        <legend>{{title}} </legend>
        <button type="button" id='select' @click="searchInstrument()">Search</button>
        <input type="text" v-model="searchInst">

<!-- 2eme option avec bootstrap modal  -->

        <div v-for="(item, name) in instrumentClass" :key="name">  
            <b-button v-b-modal="'my-modal'" @click="showInstruments(name, item)">{{name}}</b-button>
        </div>
        <b-modal id="my-modal">
            <div v-if="instrumentCategory">
                <div v-for="item in instrumentsList" :key="item">
                    <input type="checkbox" :value="item" name="instrumentSelection" v-model="instrumentSelection">
                    <label :for="item">{{item}} </label>
                </div>
            </div>
        </b-modal>
        <div v-if="showInstrument == true">
            <input type="checkbox" :value="resultSearch" name="instrumentSelection" v-model="instrumentSelection">
            <label :for="resultSearch">{{resultSearch}}</label>
        </div> 
        <p v-else-if="showInstrument == false">"Cet instrument n'est pas dans la liste"</p>        

    </fieldset>

    <!-- 2 options : premiere sans bootstrap modal -->
        <!-- <div v-for="(item, name) in instrumentClass" :key="name" class="container">
            <div class="row">
                <button type="button" class="col-3" id='select' @click="showInstruments(name).prevent">{{name}} </button>
            </div>
            <fieldset v-if="instrumentCategory === name">
                <div v-for="e in item" :key="e">
                    <input type="checkbox" :value="e" name="instrumentSelection" v-model="instrumentSelection">
                    <label :for="e">{{e}} </label>
                </div>
            </fieldset>
        </div>
        <div v-if="showInstrument == true">
            <input type="checkbox" :value="resultSearch" name="instrumentSelection" v-model="instrumentSelection">
            <label :for="resultSearch">{{resultSearch}}</label>
        </div> 
        <p v-else-if="showInstrument == false">"Cet instrument n'est pas dans la liste"</p> -->
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
        title: String
    },
}
</script>
