<template>
    <q-page>
        <h4>Agregar Productos</h4>

        <div class="col-12 col-sm-6">
            <q-input 
            standout="bg-teal text-white" 
            label="Productos" />
        </div>


        <q-form class="row q-col-gutter-md">
            <div class="col-12">
        <q-btn 
        label="Submit"
        :ripple="true"
        color="primary"/>

        <q-btn
        label="Reset"
        color="red"
        outline
        class="q-ml-sm"
        :ripple="true"
        />
            </div>
        </q-form>
    </q-page>
</template>