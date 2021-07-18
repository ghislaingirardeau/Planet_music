<template>
    <div>
        <!-- search button feature -->
        <button @click="searchInstrument">Search</button>
        <input type="text" v-model="searchInst"> 
        {{resultSearch}}  
    </div>
</template>

<script>
import instrument from '@/store/instruments'

export default {
    data() {
        return {
            searchInst: "",
            resultSearch: "",
            instrumentClass: instrument
        }
    },
    methods: {
        searchInstrument() {
          for (let i in this.instrumentClass) {
              if(this.instrumentClass[i].find(element => element === this.searchInst)) {
                 return this.resultSearch = i
              } else {
                  this.resultSearch = "Cet instrument n'est pas dans la liste"
              }
        }            
    }
  }
}
</script>
