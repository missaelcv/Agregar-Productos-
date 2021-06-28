# Quasar App (quasarv2)

A Quasar Framework app

## Install the dependencies
```bash
yarn global add @quasar/cli
npm install -g @quasar/cli
```

### Start the app in development servidor)
```bash
quasar dev
```

### Lint the files
```bash
yarn run lint
```

### Build the app for production
```bash
quasar build
```

### Customize the configuration
See [Configuring quasar.conf.js](https://v2.quasar.dev/quasar-cli/quasar-conf-js).

### Creacion de drawer 
```
<template>
  <div class="q-pa-md">
  <q-layout view="lHh Lpr lff">
      <q-header elevated class="bg-cyan-8">
        <q-toolbar>
          <q-toolbar-title>Aplicacacion Web</q-toolbar-title>
          <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        show-if-above
        :width="200"
        :breakpoint="400">

        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>

            <q-item clickable v-ripple to="/"  active-class="my-menu-link" exact>
```


## Router
```
const routes = [
  {
    path: '/',
    component: () => import('layouts/MainLayout.vue'),
    children: [
      { path: '', component: () => import('pages/Index.vue') },
      { path: '/about', component: () => import('pages/About.vue') },
      { path: '/send', component: () => import('pages/Send.vue') },
      { path: '/form', component: () => import('pages/Form.vue') }

    ]
  },
  ```
## Boton de Aceptar Terminos
```
<div class="col-12 col-sm-6">
<q-toggle
        label="Acepta los terminos"
        v-model="terminos"/>
        </div>
```
## Boton de Enviar/Submit Formulario
```
<div class="col-12">
        <q-btn 
        label="Submit"
        :ripple="true"
        color="primary"
        type="submit"/>
```

## Boton de Resert Formulario
```
<q-btn
        label="Reset"
        color="red"
        outline
        class="q-ml-sm"
        :ripple="true"
        type="reset"/>
```

## Importando ref para las constantes y userQuasar para las notify
  ```
<script>
import {ref} from 'vue'
import { useQuasar } from 'quasar'
import PintarDatos from 'src/components/PintarDatos.vue'
  ```

## Rows array
  ```
const rows = [
     {
          producto: 'producto 1',
          prioridad: 'Maxima'
     }
]
 ```

## Const de producto 
 ```
 export default {
  components: { PintarDatos },
    setup() {
        const myForm = ref(null)
       const $q = useQuasar()
        const producto = ref(null)
        const seleccion = ref(null)
        const terminos = ref (false)
        const opciones = ['maxima', 'media', 'minima']
        const productos = ref([])
```

## Constante que procesa formulario para Validar
```
  const procesarFormulario = () => {
                console.log("clic al Formulario")
                if(terminos.value === false){
                     $q.notify({
                         color: 'red-5',
                            textColor: 'white',
                            icon: 'warning',
                            message: 'Debe Aceptar Terminos y Condiciones'
                     })
                } else {
                 $q.notify({
                color: 'green-4',
                textColor: 'white',
                icon: 'cloud_done',
                message: 'Formulario Enviado'
                    })
```

## Resetear el formulario
```
  myForm.value.resetValidation()       
```
## Resetear formulario
```
 reset() 
        const reset = () => {
            producto.value = null
            seleccion.value = null
            terminos.value = false 
        }
``` 
## Opcion para mostrar al usario
```
<pre>{{producto}} - {{seleccion}} - {{terminos}}</pre>
```

## Llamando el componente para mandar los datos
``` 
  <pintar-datos :productos="productos" />
``` 

## Procesar el Formulario
```
     productos.value =[...productos.value,{
        producto: producto.value,
        prioridad: seleccion.value
        }]
```

## Creamos el props con array para el producto
 ```
export default ({
     props: {
          productos: Array
     },
     setup() {
          return{
          columns,
          rows
          }
     },
})
</script>
 ```

## Retornar
```
 return {
                producto,
                seleccion,
                opciones,
                procesarFormulario,
                terminos,
                reset,
                myForm,
                productos
               }
```

