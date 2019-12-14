<template>
<el-form :model="model":rules="rules" ref="form">
  <el-form-item label="Bitte geben Sie Ihre persönlichen Daten ein.">
  </el-form-item>
  <el-form-item label="Vorname:" prop="Vorname">
    <el-input v-model="model.Vorname" placeholder="Vorname"></el-input>
  </el-form-item>
  <el-form-item label="Nachname:" prop="Nachname">
    <el-input v-model="model.Nachname" placeholder="Nachname"></el-input>
  </el-form-item>
  <el-form-item label="Geschlecht:" prop="Geschlecht">
    <el-radio v-model="model.Geschlecht"
              v-for="lang in GeschlechtOptions"
              :key="lang.value"
              :label="lang.label"
              :value="lang.value">
          </el-radio>
  </el-form-item>
</el-form>
</template>

<script>
export default {
  data(){
		return {
      model: {
        Vorname: '',
        Nachname: '',
        Geschlecht: ''
      },
      GeschlechtOptions: [
          {value: 'Weiblich', label: ' Weiblich'},
          {value: 'Männlich', label: ' Männlich'}],
      rules: {
        Vorname: [{
          required: true,
          message: 'Pflichtfeld',
          trigger: 'blur'
        }],
        Nachname: [{
          required: true,
          message: 'Pflichtfeld',
          trigger: 'blur'
        }],
        Geschlecht: [{
          required: true,
          message: 'Pflichtfeld',
          trigger: 'change'
        }],
      }
	}},
  methods: {
    validate() {
      return new Promise((resolve, reject) => {
        this.$refs.form.validate((valid) => {
          this.$emit('on-validate', valid, this.model)
          resolve(valid);
        });
      })

    }
  }

}
</script>

<style>

</style>
