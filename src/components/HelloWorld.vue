<template>

<div style="display: flex; width: '100%'';">
  <tk-dropdown
      :options="countries"
      :selectedOption="selectedCountry"
      :placeholder="'Select Country'"
      :width="'25%'"
      @update:selectedOption="onCountrySelected"
    />
    <tk-dropdown
      :options="languages"
      :selectedOption="selectedLanguage"
      :placeholder="'Select Language'"
      :width="'45%'"
      @update:selectedOption="onLanguageSelected"
    />
</div>

 
  
</template>

<script>
import TkDropdown from './tk-dropdown.vue'; // tk-dropdown componentinin import edildiği yer ve dosya yolu



export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    TkDropdown
  },
  data() {
    return {
      countries: [
        { icon: 'flag-au', text: 'Australia' },
        { icon: 'flag-gr', text: 'Germany' },
        { icon: 'flag-fr', text: 'France' }
      ],
      selectedCountry: null,
      languages: [
        { icon: 'flag-au', text: 'Türkçe' },
        { icon: 'flag-gr', text: 'Lazca' },
        { icon: 'flag-fr', text: 'Farsça' }
      ],
      selectedLanguage: null
    };
},
methods: {
  onCountrySelected(option) {
        this.selectedCountry = option;
    },
    onLanguageSelected(option) {
        this.selectedLanguage = option;
    }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

</style>
