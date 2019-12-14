<template>
<div id="app">
  <img src="./assets/logo.png">
<div>
        <form-wizard @on-complete="onComplete" step-size="xs"
                      :start-index="0"
                      title="LeWizard Fragebogen"
                      subtitle="Bitte füllen Sie das folgende Formular aus"
                      shape="circle"
                      back-button-text="Zurück"
                      next-button-text="Weiter"
                      finish-button-text="Fertig"
                      color="#42b983">
            <tab-content title="Erster Schritt"
            :before-change="() => validate('ErsterS')">
        <Erster-s ref="ErsterS" @on-validate="onStepValidate"></Erster-s>
            </tab-content>
            <tab-content title="Zweiter Schritt"
              :before-change="() => validate('ZweiterS')">
        <Zweiter-s ref="ZweiterS" @on-validate="onStepValidate"></Zweiter-s>
            </tab-content>
            <tab-content title="Dritter Schritt"
            :before-change="() => validate('DritterS')">
        <Dritter-s ref="DritterS" @on-validate="onStepValidate"></Dritter-s>
            </tab-content>
            <tab-content title="Vierter Schritt"
            :before-change="() => validate('VierterS')">
               <Vierter-s ref="VierterS" @on-validate="onStepValidate"></Vierter-s>
            </tab-content>
            <tab-content title="Letzte Schritt"
             :before-change="() => validate('FunfterS')">
             <pre v-html="Lewizard"></pre>
        <Funfter-s ref="FunfterS" @on-validate="onStepValidate"></Funfter-s>
            </tab-content>
        </form-wizard>
 </div>
</div>
</template>

<script>
  import ErsterS from './components/ErsterS.vue'
  import ZweiterS from './components/ZweiterS.vue'
  import DritterS from './components/DritterS.vue'
  import VierterS from './components/VierterS.vue'
  import FunfterS from './components/FunfterS.vue'
  import Lewizard from './Lewizard.js'
	export default {
	name: 'app',
	components: {
     ErsterS,
     ZweiterS,
     DritterS,
     VierterS,
     FunfterS
	},
	data(){
		return {
		 finalModel: {}	
		}
  },
  computed: {
		Lewizard(){
			return Lewizard(this.finalModel)
		}
	},
  methods: {
    onComplete() {
      alert('Endlich!');
    },
    validate(ref) {
      return this.$refs[ref].validate()
    },
		onStepValidate(validated, model){
			if(validated){
       this.finalModel = {...this.finalModel, ...model}
        }
      }
    }
  }
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
