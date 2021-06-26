<template>
    <q-page>
        <h4>Agregar Productos</h4>

        <pre>{{productos}} - {{seleccion}} - {{terminos}}</pre>

         <q-form 
         class="row q-col-gutter-md"
         @submit.prevent="procesarFormulario"
         >

         <div class="col-12 col-sm-6">
            <q-input  
            label="Productos" 
            v-model="productos"
            :rules="[ val => val && val.length > 0 || 'No puede Estar el blanco']"
          
            
            />
        </div>

        <div class="col-12 col-sm-6">
            <q-select
             label="Prioridad" 
             v-model="seleccion"
            :options = "opciones"
             :rules="[ val => val && val.length > 0 || 'Please type something']"
             />    
        </div>

        <div class="col-12 col-sm-6">

        <q-toggle
        label="Acepta los terminos"
        v-model="terminos"
        />
        </div>

        <div class="col-12">
        <q-btn 
        label="Submit"
        :ripple="true"
        color="primary"
        type="submit"/>

        <q-btn
        label="Reset"
        color="red"
        outline
        class="q-ml-sm"
        :ripple="true"
        type="reset"
        />
            </div>
        </q-form>
    </q-page>
</template>

<script>
import {ref} from 'vue'

export default {
    setup() {
        const productos = ref(null)
        const seleccion = ref(null)
        const terminos = ref (false)
        const opciones = ['maxima', 'media', 'minima']
        const procesarFormulario = () => {
                console.log("clic al Formulario")
        }
      

        return {
                productos,
                seleccion,
                opciones,
                procesarFormulario,
                terminos
               
    }
},
}
</script>
