<template>
    <q-page>
        <h4>Agregar Productos</h4>

        <pre>{{productos}} - {{seleccion}} - {{terminos}}</pre>

         <q-form 
         class="row q-col-gutter-md"
         @submit.prevent="procesarFormulario"
         @reset="reset"
         ref="myForm"
         >

         <div class="col-12 col-sm-6">
            <q-input  
            label="Productos" 
            v-model="productos"
              lazy-rules
            :rules="[ val => val && val.length > 0 || 'No puede Estar el blanco']"
          
            
            />
        </div>

        <div class="col-12 col-sm-6">
            <q-select
             label="Prioridad" 
             v-model="seleccion"
            :options = "opciones"
              lazy-rules
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
import { useQuasar } from 'quasar'
import { Notify } from 'quasar'

export default {
    setup() {
        const myForm = ref(null)
       const $q = useQuasar()
        const productos = ref(null)
        const seleccion = ref(null)
        const terminos = ref (false)
        const opciones = ['maxima', 'media', 'minima']

        Notify.create({
        message: 'Danger, Will Robinson! Danger!'
        })

        const procesarFormulario = () => {
                console.log("clic al Formulario")
                if(terminos.value === false){
                     $q.notify({
                         color: 'red-5',
                            textColor: 'white',
                            icon: 'warning',
                            message: 'You need to accept the license and terms first'
                     })
                } else {
                 $q.notify({
                color: 'green-4',
                textColor: 'white',
                icon: 'cloud_done',
                message: 'Submitted'
                    })
                 myForm.value.resetValidation()
                    reset()
                }
        }
        const reset = () => {
            productos.value = null
            seleccion.value = null
            terminos.value = false 
 
        } 
     

        return {
                productos,
                seleccion,
                opciones,
                procesarFormulario,
                terminos,
                reset,
                myForm
               
    }
},
}
</script>
