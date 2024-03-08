<template>
  <div id="app">
    <form @submit.prevent="onSubmit">
      <h2 style="text-align: center; top: 20px; position: relative;">DATOS PERSONALES</h2><br>
      <b-row style="background-color: rgba(169, 172, 172, 0.717); height: 250px; margin: 5px; border-radius: 15px;">
        <b-col cols="4">
          <label>Nombre/s</label>
          <b-form-input v-validate="'required:true|alpha_spaces'" name="nombres" v-model="nombres" type="text" />
          <span style="color: brown;">{{ errors.first('nombres') }}</span>
        </b-col>
        <b-col cols="4">
          <label>Apellidos</label>
          <b-form-input v-validate="'required|alpha_spaces'" name="apellidos" v-model="apellidos" type="text" />
          <span style="color: brown;">{{ errors.first('apellidos') }}</span>
        </b-col>
        <b-col cols="4">
          <label>Fecha de Nacimiento</label>
          <b-form-input v-validate="'required|date_format:dd/MM/yyyy|date_between:10/09/1954,12/12/2005'" name="fechaNac"
            v-model="fechaNac" type="text" />
          <span style="color: brown;">{{ errors.first('fechaNac') }}</span>
        </b-col>
        <b-col cols="4">
          <label>NSS</label>
          <b-form-input v-validate="'required|digits:11'" name="nss" v-model="nss" type="text" />
          <span style="color: brown;">{{ errors.first('nss') }}</span>
        </b-col>
        <b-col cols="4">
          <label>CURP</label>
          <b-form-input v-validate="'required|alpha_num|max:18'" name="curp" v-model="curp" type="text" />
          <span style="color: brown;">{{ errors.first('curp') }}</span>
        </b-col>
        <b-col cols="4">
          <label>Telefono</label>
          <b-form-input v-validate="'required|digits:10'" name="telefono" v-model="telefono" type="text" />
          <span style="color: brown;">{{ errors.first('telefono') }}</span>
        </b-col>
        <b-col cols="4">
          <label>Dirección</label>
          <b-form-input v-validate="'required'" name="direccion" v-model="direccion" type="text" />
          <span style="color: brown;">{{ errors.first('direccion') }}</span>
        </b-col>
        <b-col cols="4">
          <label>Tarjeta de Credito/Debito</label>
          <b-form-input v-validate="'required|credit_card'" name="tarjeta" v-model="tarjeta" type="text" />
          <span style="color: brown;">{{ errors.first('tarjeta') }}</span>
        </b-col>
        <b-col cols="4">
          <br>
          <div>
            <b-form-select style="border-radius: 7px; width: 390px; height: 35px;" v-model="genero"  v-validate="'included:Femenino,Masculino'" name="genero" >
                <b-form-select-option   value="No">Seleccions tu Sexo</b-form-select-option>
                <b-form-select-option value="Femenino">Femenino</b-form-select-option>
                <b-form-select-option value="Masculino">Masculino</b-form-select-option>
            </b-form-select >
          </div>
            <span style="color: brown;">{{ errors.first('genero') }}</span>
        </b-col>
      </b-row>

      <h2 style="text-align: center; top: 20px; position: relative;">DATOS DE LA CUENTA</h2><br>
      <b-row style="background-color: rgba(169, 172, 172, 0.717); height: 250px; margin: 5px; border-radius: 15px;">
        <b-col cols="6">
          <label>Correo Electronico</label>
          <b-form-input v-validate="'required|email'" name="email" v-model="email" type="email" />
          <span style="color: brown;">{{ errors.first('email') }}</span>
        </b-col>
        <b-col cols="6">
          <label>Nombre de usuario</label>
          <b-form-input v-validate="'required|alpha_dash'" name="usuario" v-model="usuario" type="text" />
          <span style="color: brown;">{{ errors.first('usuario') }}</span>
        </b-col>

        <b-col cols="6">
          <label>Contraseña </label>
          <b-form-input v-validate="'required|alpha_dash|min:7'" name="password" v-model="contrasena" type="password"
            :class="{ 'is-danger': errors.has('password') }" ref="password" />
          <span style="color: brown;" v-show="errors.has('password')" class="help is-danger">{{ errors.first('password')
          }}</span>
        </b-col>
        <b-col cols="6">
          <label>Confirmar Contraseña </label>
          <b-form-input v-validate="'required|confirmed:password'" name="password_confirmation" v-model="contrasena_again" type="password"
            :class="{ 'is-danger': errors.has('password_confirmation') }" data-vv-as="password" />
          <span style="color: brown;" v-show="errors.has('password_confirmation')" class="help is-danger">{{
            errors.first('password_confirmation') }}</span>
        </b-col>

      </b-row>

      <b-button variant="success" type="submit">Enviar</b-button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      nombres: '',
      apellidos: '',
      fechaNac: '',
      nss: '',
      curp: '',
      telefono: '',
      direccion: '',
      tarjeta: '',
      genero: 'No',
      email: '',
      contrasena: '',
      contrasena_again:'',
      usuario: ''
      ,
      optionsSelect: [
        { value: 'Mascualino', text: 'Masculino' },
        { value: 'Femenino', text: 'Femenino' },
        { value: null, text: 'Selecciona tu genero' }
      ]
    }
  },
  methods: {
    onSubmit() {
      this.$validator.validate().then(valid => {
        if (!valid) {
         console.log('Falta Acompletar campos')
         alert('Debes de Completar todos los campos')
        }else{
          console.log('Todo corecto')
         console.log(this.$data)
         console.log(this.genero)
        }
      });
    }
  }
};
</script>
<style></style>