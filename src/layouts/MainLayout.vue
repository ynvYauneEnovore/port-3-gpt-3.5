<template>
  <q-layout view="lHh Lpr lFf">
    <q-header style="background-color: rgba(1,31,43,0.81);">
      <q-toolbar>
        
        <q-toolbar-title>
          <h1 class="text-h5"><q-spinner-grid color="teal"></q-spinner-grid> Port-3 </h1> 
        </q-toolbar-title>

        
        
        <q-btn-dropdown
        
        
      class="glossy"
      label="DEV"
    >
      <div class="row no-wrap q-pa-md">
        <div class="column">
          <div class="text-h6 q-mb-md">Información</div>
          <q-toggle color="positive" v-model="mobileData" label="Disponible"/>
          <q-toggle v-model="bluetooth" label="Bluetooth" />
          <br><q-separator inset /><br>
          
          <q-btn
          
      padding="xs lg"
      color="positive"
      round
    >

    <q-spinner-comment
        color="dark"
        size="2em"
      />
        </q-btn>
        </div>

        <q-separator vertical inset class="q-mx-lg" />

        <div class="column items-center">
          <q-avatar size="72px">
            <img src="img/perf.png">
          </q-avatar>

          <div class="text-subtitle1 q-mt-md q-mb-xs">Yovan Ramón Yaune Enovore</div><br>
       
          <q-btn color="positive" @click="persistent = true">
             ir   \   system<q-spinner-gears
        color="dark"
        size="2.5em"
      />
          </q-btn>

<q-dialog v-model="persistent" persistent transition-show="scale" transition-hide="scale">
  <q-card class="bg-teal text-white" style="width: 300px">
    <q-card-section>
      <div class="text-h6">Acceder al sistema de principal</div>
    </q-card-section>

    <q-card-section class="q-pt-none">
      Mi sistema principal es un espacio privado y seguro donde almaceno y gestiono todos mis recursos digitales y sistemas.
       Cuenta con medidas avanzadas de seguridad y está diseñado para ser escalable y confiable. 
       Esto me permite acceder a mis archivos y recursos de manera eficiente y protegerlos de posibles amenazas externas.
    </q-card-section>

    <q-card-section class="q-pt-none">
      (Haga click/toque en ATRAS para salir. )
    </q-card-section>

    <q-card-actions align="right" class="bg-white text-teal">
      <q-btn color="positive" flat label="ir" v-close-popup @click="IP_YNV"/>
      <q-btn color="negative" flat label="Atras" v-close-popup/>
    </q-card-actions>
  </q-card>
</q-dialog>

          
      </div>
    </div>
    </q-btn-dropdown>
    <q-page-sticky position="bottom-right" :offset="[18, 18]">
            <q-fab
              icon="add"
              direction="up"
              color="accent"
            >
            <ion-icon name="logo-whatsapp"></ion-icon> 
            <q-fab-action @click="onClick" color="primary" icon="person_add" />
            <q-fab-action @click="onClick" color="primary" icon="mail" />
            <q-fab-action @click="onClick" color="primary" icon="phone" />
            </q-fab>
          </q-page-sticky>
        
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
  
</template>

<script>
import { defineComponent, ref } from 'vue'


export default defineComponent({
  methods: {
    IP_YNV () {
      window.location.href = 'http://192.168.1.1'
    }
  },

  name: 'MainLayout',

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      persistent: ref(false),
      onClick () {
        console.log('Clicked on a fab action')
      },
      mobileData: ref(true),
      bluetooth: ref(true),
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
