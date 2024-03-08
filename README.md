# Validacion de Formularios con Vee-Validate

Para instalar esta libreria utiliza el siguiente comando

```sh
npm install vee-validate@2 --save
```

## En el Archivo main.js

Se debe de importar 
```sh
import VeeValidate , { Validator }  from 'vee-validate'
```

## Para cambiar el idioma de los mensajes debes de usar Validator y localize de esta mamera.

```sh
Validator.localize('es', {
  messages: {
    alpha: () => 'Este campo solo puede contener letras.',
    alpha_spaces: 'Solo acepta letras y espacios',
    min : (field,[num])=>`Debe de contener ${num} caracteres como minimo`,
    included:"Debes de selccionar una opcion (Masculino/Femenino)"
  }
});
```

## Introducción 

Para cada campo del formulario  debes de implementar la siguiente directiva personalidaza(v-validate) para que vee-validate controle la validación.
Existen  muchas  reglas de validación listas para usar y todas están localizadas y cubren la mayoría de las necesidades de validación, solo con usar el nombre de la rgla, por ejemplo:

**alfa:** El campo bajo validación solo puede contener caracteres alfabéticos.

**alfa_dash:** El campo bajo validación puede contener caracteres alfabéticos, números, guiones o guiones bajos.

**número_alfa:** El campo bajo validación puede contener caracteres alfabéticos o números.


### implentación

```sh
<input v-validate="'alpha_dash'" name="alpha_dash_field" type="text">
<span style="color: brown;">{{ errors.first('alpha_dash_field') }}</span>
```
```sh
<input v-validate="'alpha'" name="alpha_field" type="text">
<span style="color: brown;">{{ errors.first('alpha_field') }}</span>
```
### Funcion validate()
Para controlar los eventos cada que se manden el formulario, se debe de colocar el siguiente metodo validate(), este metodo muestra todas las alertas de los campos que falten por llenar. Con ello puedes controlar el envio de información aplicando una estructura if.

### Implementación
```sh
 onSubmit() {
      this.$validator.validate().then(valid => {
        if (!valid) {
         console.log('Falta Acompletar campos')
        }else{
          console.log('Todo corecto')
    //Resto de código a ejecutar
        }
      });
    }
```
