<template>
<el-form :model="model":rules="rules" ref="form">
    <el-form-item label="Bitte geben Sie Ihre E-Mail-Adresse ein und akzeptieren Sie die allgemeinen Geschäftsbedingungen, um die Fragebogen abzuschließen">
  </el-form-item>
  <el-form-item label="Email:" prop="email">
    <el-input v-model="model.email" placeholder="Email"></el-input>
  </el-form-item>
  <el-form-item label="Ich akzeptiere die Allgemeinen Geschäftsbedingungen der GetSafe Insurance GmbH und bestätige, dass ich die in Ziffer 4 enthaltene datenschutzrechtliche Einwilligungserklärung zur Kenntnis genommen habe und mit der dort beschriebenen Nutzung meiner Daten einverstanden bin. Die Datenschutzhinweise für die Verwendung personenbezogener Daten habe ich zur Kenntnis genommen. Die Erstinformation erhalte ich per E-Mail zugesandt." prop="terms">
   <el-checkbox v-model="model.terms">
          </el-checkbox>
  </el-form-item>
</el-form>
</template>

<script>
export default {
  data(){
		return {
     model: {
         email: '',
      terms: ''
      },
      rules: {
          email: [{
         required: true,
         message: 'Pflichtfeld',
         trigger: 'blur'
       },
       {
         type: 'email',
         message: 'Flasche email',
         trigger: 'change'
       }],
        terms: [{
          required: true,
          message: 'Pflichtfeld',
          trigger: 'change'
        }],
        }
        }
	},
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
