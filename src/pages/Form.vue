<template>
    <q-page>
        <h4>Agregar Productos</h4>

        <pre>{{producto}} - {{seleccion}} - {{terminos}}</pre>

         <q-form 
         class="row q-col-gutter-md"
         @submit.prevent="procesarFormulario"
         @reset="reset"
         ref="myForm"
         >

         <div class="col-12 col-sm-6">
            <q-input  
            label="productos" 
            v-model="producto"
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

       <pintar-datos :productos="productos" />

    </q-page>
</template>

<script>
import {ref} from 'vue'
import { useQuasar } from 'quasar'
import PintarDatos from 'src/components/PintarDatos.vue'

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

                 myForm.value.resetValidation()       
                  

                  //Procesar el Formulario
                  productos.value =[...productos.value,{
                      producto: producto.value,
                      prioridad: seleccion.value
                  }]
                  reset() 
                }
        }
        const reset = () => {
            producto.value = null
            seleccion.value = null
            terminos.value = false 
 
        } 
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
},
}
</script>
