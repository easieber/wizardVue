<template>
<el-form :model="model":rules="rules" ref="form">
    <el-form-item label="Bitte geben Sie Ihre Website (genaue URL) und die Sprache an, in der sich die Website befindet.">
  </el-form-item>
  <el-form-item label="Website:" prop="website">
    <el-input type="url" v-model="model.website" placeholder="Website"></el-input>
  </el-form-item>
  <el-form-item label="Sprache:" prop="Sprache">
    <el-select v-model="model.language">
            <el-option v-for="lang in languageOptions"
                       :key="lang.value"
                       :label="lang.label"
                       :value="lang.value">
            </el-option>
          </el-select>
  </el-form-item>

</el-form>
</template>

<script>
export default {
  data(){
		return {
      model: {
        language: '',
        website: ''
      },
      languageOptions: [
          {value: '', label: '- Sprache -'},
          {value: 'danisch', label: 'Dansk'},
          {value: 'deutsch', label: 'Deutsch'},
          {value: 'englisch', label: 'English'},
          {value: 'spanisch', label: 'Español'},
          {value: 'franzosisch', label: 'Français'},
          {value: 'italienisch', label: 'Italiano'},
          {value: 'polisch', label: 'Polski'},
          {value: 'portuguesisch', label: 'Português'},
          {value: 'turkisch', label: 'Türkçe'},
          {value: 'russisch', label: 'Русский'},
          {value: 'japanisch', label: '日本語'},
          {value: 'koreanisch', label: '한국어'}],
      rules: {
        language: [{
          required: true,
          message: 'Pflichtfeld',
          trigger: 'change'
        }],
         website: [{
          required: true,
          message: 'Pflichtfeld',
          trigger: 'blur'
        },
        {
          type: 'url',
          message: 'Falsche url',
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
