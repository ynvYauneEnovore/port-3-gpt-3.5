<template>
  <q-layout view="lHh Lpr lFf">
    <q-header style="background-color: rgba(1,31,43,0.81);">
      <q-toolbar>
        
        <q-toolbar-title>
          <q-spinner-grid color="teal"></q-spinner-grid> Port-3
        </q-toolbar-title>
        
        <q-btn-dropdown
        
      class="glossy"
      label="Usuario"
    >
      <div class="row no-wrap q-pa-md">
        <div class="column">
          <div class="text-h6 q-mb-md">Ingresar</div>
          <q-toggle v-model="mobileData" label="Use Mobile Data" />
          <q-toggle v-model="bluetooth" label="Bluetooth" />
        </div>

        <q-separator vertical inset class="q-mx-lg" />

        <div class="column items-center">
          <q-avatar size="72px">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png">
          </q-avatar>

          <div class="text-subtitle1 q-mt-md q-mb-xs">Yovan R. Y. E.</div>

          
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
  name: 'MainLayout',

  setup () {
    const leftDrawerOpen = ref(false)

    return {
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
