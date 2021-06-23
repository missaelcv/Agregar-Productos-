<template>
        <q-page padding>
            <h3>Hola Send</h3>

            <div class="q-pa-md">
            <div class="q-gutter-x-md">
                
             <q-btn color="primary" label="Uno" v-for="n in 1" :key="n" />
             <q-btn color="green" label="Dos" v-for="n in 1" :key="n" />
             <q-btn color="red" label="Tres" v-for="n in 1" :key="n" />
             <q-btn color="purple" label="Cuatro" v-for="n in 1" :key="n" />
    </div>
  </div>

            <div class="row">
            <p class="col 12 col-sm-6 col-md-3">Lorem ipsum dolor sit amet consectetur, adipisicing elit. 
            Maxime sint voluptatem ad voluptatibus. Ut aspernatur ipsam aut totam,
            quasi dignissimos odit deleniti repellendus nobis laboriosam doloribus
            nesciunt. Sequi, nostrum architecto.</p>
            
            <p class="col 12 col-md-6">Lorem ipsum dolor sit amet consectetur, adipisicing elit. 
            Maxime sint voluptatem ad voluptatibus. Ut aspernatur ipsam aut totam,
            quasi dignissimos odit deleniti repellendus nobis laboriosam doloribus
            nesciunt. Sequi, nostrum architecto.</p>

            <p class="col 12 col-md-6">Lorem ipsum dolor sit amet consectetur, adipisicing elit. 
            Maxime sint voluptatem ad voluptatibus. Ut aspernatur ipsam aut totam,
            quasi dignissimos odit deleniti repellendus nobis laboriosam doloribus
            nesciunt. Sequi, nostrum architecto.</p>

            <div class="row items-center bg-dark text-white"
             style="height: 300px">
            <p class="col bg-positive">One of three cols</p>
            <p class="col bg-positive">One of three cols</p> 
            <p class="col bg-positive">One of three cols</p>
            </div>
            </div>
        </q-page>
</template>