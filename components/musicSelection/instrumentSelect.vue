<template>
    <fieldset class="row m-3">
        <legend class="col-12">{{title}} </legend>

        <!-- BLOC RECHERCHE INSTRUMENT -->
        <aside class="col-12 mb-4 text-center">

            <input class="col-5" type="text" v-model="searchInst" placeholder="Rechercher un instrument" v-on:keyup.enter="searchInstrument()">
            <button type="button" id='select' @click="searchInstrument()">Search</button>
            
            <div class="col-12 mt-3" v-if="showInstrument == true">
                <input type="checkbox" :value="resultSearch" name="instrumentSelection" v-model="instrumentSelection">
                <label :for="resultSearch">{{resultSearch}}</label>
            </div> 
        
            <p class="m-3" v-else-if="showInstrument == false">"Cet instrument n'est pas dans la liste"</p>
            
        </aside>

        <!-- BOUTON MODAL CATEGORIE INSTRUMENT -->
        <div class=" col-4 text-center mb-3" v-for="(item, name) in instrumentClass" :key="name">  
            <b-button v-b-modal="'my-modal'" @click="showInstruments(name, item)">{{name}}</b-button>
        </div>

        <!-- AFFICHAGE DU MODAL ET LISTE INSTRUMENTS -->
        <b-modal id="my-modal" title="Sélectionner votre instrument">
            <div v-if="instrumentCategory">
                <div v-for="item in instrumentsList" :key="item">
                    <input type="checkbox" :value="item" name="instrumentSelection" v-model="instrumentSelection">
                    <label :for="item">{{item}} </label>
                </div>
            </div>
        </b-modal>

        <!-- AFFICHE INSTRUMENT VALIDER ET BOUTON -->
        <div class="col-12">
            
            <strong class="d-block mb-4">{{instrumentSelected}}</strong>
            <button @click="next">Valider</button>

        </div>

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
        instrumentSelected() {
            return "Mes instruments préférés: " + this.instrumentSelection.join(', ')
        }
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
