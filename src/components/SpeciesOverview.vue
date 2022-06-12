<template>
  <div class="overview">
    <div v-for="data in species" :key="data.s"><h1>{{data.name}} </h1>

      <div class="creatureNamer" @change="generatePreview(data.s)">
        <select v-model="selected[index]" v-for="(value, propertyName, index) in data.props" :key="value.id" >
          <option v-for="(gene, index) in value.Gene" :key="gene.id" 
                  :name="propertyName" 
                  :value="{id: index, property: propertyName, code: gene.Code, nomenclature: gene.Nomenclature}">
            {{index+1}} {{gene.Code}}
          </option>
        </select>
      </div>
      <div class="finalName">
        <span v-for="slice in selected" :key="slice.key">{{slice.nomenclature}}</span>
      </div>
      <img :src="previewURL"/>
    </div>
  </div>
</template>

<script>
import speciesData from '../../species.json'
export default {
  name: 'SpeciesOverview',
  data() {
    return {
      species: speciesData.species,
      images: [],
      selected: {},
      previewURL: "",
      sex: "male"
    };
  },
  methods: {
    generatePreview: function(id) {
      var url = "https://finaloutpost.net/ln?s=" + id + "&c=";
      var selectedCombination = this.selected;
      Object.keys(selectedCombination).forEach(function(key) {
        var slice = selectedCombination[key];
        url += slice.property + ":" + slice.code + ",";
      });
      url = url.slice(0, -1);
      url += "&g=male"
      this.previewURL = url;
      
    }
  },
  components: {
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.overview {
  width: 100%;
  max-width: 850px;
  margin: 0 auto;
}
.creatureNamer {
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100px;
}

.finalName {
  font-size: 110%;
  border: 2px solid #121212;
  border-radius: 5px;
  padding: 10px 0;
}

.creatureNamer select {
  font-size: 120%;
  padding: 5px;
  text-align: center;
}

.creatureList {
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: center;
}

.creatureList > * {
  flex: 0 0 5%;
}

</style>
