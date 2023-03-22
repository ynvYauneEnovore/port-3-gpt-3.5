<template>
  <q-page class="">
    <div class="q-pa-md">
      <div class="q-pa-md">
    <q-carousel
      v-model="slide"
      transition-prev="scale"
      transition-next="scale"
      swipeable
      animated
      control-color="white"
      navigation
      padding
      arrows
      height="300px"
      class="bg-primary text-white shadow-1 rounded-borders"
    >
      <template v-slot:navigation-icon="{ active, btnProps, onClick }">
        <q-btn v-if="active" size="lg" icon="home" color="yellow" flat round dense @click="onClick" />
        <q-btn v-else size="sm" :icon="btnProps.icon" color="white" flat round dense @click="onClick" />
      </template>

      <q-carousel-slide name="style" class="column no-wrap flex-center">
        <q-icon name="style" size="56px" />
        <div class="q-mt-md text-center">
          {{ lorem1 }}
        </div>
      </q-carousel-slide>
      <q-carousel-slide name="tv" class="column no-wrap flex-center">
        <q-icon name="live_tv" size="56px" />
        <div class="q-mt-md text-center">
          {{ lorem2 }}
        </div>
      </q-carousel-slide>
      <q-carousel-slide name="layers" class="column no-wrap flex-center">
        <q-icon name="layers" size="56px" />
        <div class="q-mt-md text-center">
          {{ lorem3 }}
        </div>
      </q-carousel-slide>
      <q-carousel-slide name="map" class="column no-wrap flex-center">
        <q-icon name="terrain" size="56px" />
        <div class="q-mt-md text-center">
          {{ lorem4 }}
        </div>
      </q-carousel-slide>
    </q-carousel>
  </div>
  
    <q-card class="my-card">
      <q-parallax
        src="img/yovan-1.png"
        :height="150"
      />

      <q-card-section>
        <div class="text-h6">Our Changing Planet</div>
        <div class="text-subtitle2">by John Doe</div>
      </q-card-section>
    </q-card>
  </div>
  </q-page>


  
  <q-footer reveal elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <div>Yovan Ramón Yaune Enovore &copy; 2023</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      slide: ref('style'),
      lorem1: 'Hola1.',
      lorem2: 'Hola4.',
      lorem3: 'Hola3.',
      lorem4: 'Hola2.'
    }
  }
}

</script>






