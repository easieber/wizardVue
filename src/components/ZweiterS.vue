<template>
<el-form :model="model":rules="rules" ref="form">
  <el-form-item label="Bitte wählen Sie Ihren Geburtstag">
    </el-form-item>
<el-form-item label="Datum:" prop="Datum">
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <date-picker v-model="Datum" :value="value"></date-picker>
      </div>
    </div>
  </div>
  </el-form-item>
  </el-form>
</template>

<script>
  import 'bootstrap/dist/css/bootstrap.css';
  import datePicker from 'vue-bootstrap-datetimepicker';
  import 'eonasdan-bootstrap-datetimepicker/build/css/bootstrap-datetimepicker.css';
   
  export default {    
    data () {
      return {
        date: new Date(),
        value: {
          format: 'DD/MM/YYYY',
          useCurrent: false,
        },
       model: {
        Datum: 'date'
      },       
      }
    },
    components: {
      datePicker
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