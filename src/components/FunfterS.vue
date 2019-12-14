<template>
<el-form :model="model":rules="rules" ref="form">
    <el-form-item label="Überprüfen Sie Ihre Daten und prüfen Sie, ob sie korrekt sind, wählen Sie das Feld aus und klicken Sie dann auf Fertig, um zu beenden">
  </el-form-item>
  <el-form-item label="" prop="fertig">
   <el-checkbox v-model="model.fertig">
          </el-checkbox>
  </el-form-item>
  </el-form>
</template>

<script>
export default {
  data(){
		return {
     model: {
      fertig: ''
      },
      rules: {
        fertig: [{
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