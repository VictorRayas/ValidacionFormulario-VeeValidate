# Validación de Formularios con Vee-Validate

Para instalar esta libreria utiliza el siguiente comando

```sh
npm install vee-validate@2 --save
```

## En el Archivo main.js

Se debe de importar 
```sh
import VeeValidate , { Validator }  from 'vee-validate'
```

## Para cambiar el idioma de los mensajes debes de usar Validator y localize() de esta mamera.

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

**alpha:** Esta función valida que el campo solo contenga letras (sin espacios ni otros caracteres).

**alpha_spaces:** Permite letras y espacios, pero no caracteres especiales.

**required**: Verifica si el campo está vacío o no. Si está vacío, devuelve un mensaje indicando que el campo es obligatorio.

**digits:** Verifica si el campo tiene el número de dígitos especificado y si son números.

**date_format:** Valida si la fecha tiene el formato correcto (por ejemplo, dd/MM/yyyy).

**date_between:** Verifica si la fecha está dentro de un rango específico.

**alpha_num:** Acepta solo letras y números, no caracteres especiales.

**max:** Valida si el campo tiene un valor que no excede un máximo dado.

**credit_card** Verifica si el número ingresado se parece a un número de tarjeta de crédito o débito válido.

**email:** Valida si la entrada se parece a una dirección de correo electrónico válida.

**alpha_dash:** Acepta solo caracteres alfanuméricos, guiones y guiones bajos.

**min:** Verifica si el campo tiene un número mínimo de caracteres.

**included**: Verifica si el campo está incluido en un conjunto de valores específico (por ejemplo, "Masculino" o "Femenino").

 

### Implementación

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
### Para mayor información acerca de las validaciones y ejemplos de como fuciona cada campo visita la documentación.
[Documentación de Vee-Validate](https://vee-validate.logaretm.com/v2/guide/rules.html#after)
