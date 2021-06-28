<template>

 <pre>{{productos}}</pre>

     <q-table
     class="q-mt-md"
     no-data-label="sin productos a la vista"
     title="Productos"
     :columns="columns"
     :rows="productos"

     />
</template>

<script>

const columns = [

     {
    name: 'producto',
    required: true,
    label: 'Producto',
    align: 'left',
    field: 'producto',
    sortable: true
     },

     {
    name: 'prioridad',
    required: true,
    label: 'Prioridad',
    align: 'left',
    field: 'prioridad',
    sortable: true
     }
]

const rows = [
     {
          producto: 'producto 1',
          prioridad: 'Maxima'
     }
]


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
