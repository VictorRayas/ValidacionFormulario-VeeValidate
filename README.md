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

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
