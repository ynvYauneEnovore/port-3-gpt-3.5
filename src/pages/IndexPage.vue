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
      class="bg-dark text-white shadow-1 rounded-borders"
    >
      <template v-slot:navigation-icon="{ active, btnProps, onClick }">
        <q-btn v-if="active" size="lg" icon="home" color="yellow" flat round dense @click="onClick" />
        <q-btn v-else size="sm" :icon="btnProps.icon" color="white" flat round dense @click="onClick" />
      </template>

      <q-carousel-slide name="style" class="column no-wrap flex-center">
        <img src="img/logo.png" :height="290">
        <div class="q-mt-md text-center">
        </div>
      </q-carousel-slide>
      <q-carousel-slide name="tv" class="column no-wrap flex-center">
        <img src="img/v.png" :height="290">
        <div class="q-mt-md text-center">
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
        <div class="text-h6">Mi enfoque se basa en la combinación de habilidades creativas y técnicas, para lograr un resultado impresionante y funcional. Ya sea que se trate de diseño gráfico, desarrollo web o ambas cosas, me aseguro de que el resultado final sea de la más alta calidad.</div>
        <div class="text-subtitle2">by Yovam Yaune</div>
        <q-avatar rounded>
          <img src="https://cdn.quasar.dev/img/chaosmonkey.png">
        </q-avatar>
      </q-card-section>
    </q-card>

 
    <q-video
      :ratio="16/9"
      src="https://www.youtube.com/embed/ml-npkj_LxM"
    />
  
  </div>
  </q-page>

  <div class="q-pa-md">
    <q-parallax :height="150">
      <template v-slot:media>
        <video width="720" height="440" poster="https://cdn.quasar.dev/img/polina.jpg" autoplay loop muted>
          <source type="video/webm" src="https://cdn.quasar.dev/img/polina.webm">
          <source type="video/mp4" src="https://cdn.quasar.dev/img/polina.mp4">
        </video>
      </template>

      <h3 class="text-white">Video</h3>
    </q-parallax>
  </div>
  

  <div class="q-pa-md">
    <q-parallax>
      <template v-slot:media>
        <img src="img/card-3.png">
      </template>

      <template v-slot:content="scope">
        <div
          class="absolute column items-center"
          :style="{
            opacity: 0.45 + (1 - scope.percentScrolled) * 0.55,
            top: (scope.percentScrolled * 60) + '%',
            left: 0,
            right: 0
          }"
        >
          <img src="img/v.png" style="width: 150px; height: 150px">
          <div class="text-h3 text-white text-center">Portafolio - Personal - Yovan</div>
          <div class="text-h6 text-grey-3 text-center">
            v3.0.4
          </div>
        </div>
      </template>
    </q-parallax>
  </div>

  <div>
    <q-splitter
      v-model="splitterModel"
      style="height: 400px"
    >

      <template v-slot:before>
        <div class="q-pa-md">
          <q-tree
            :nodes="simple"
            node-key="label"
            selected-color="primary"
            v-model:selected="selected"
            default-expand-all
          />
        </div>
      </template>

      <template v-slot:after>
        <q-tab-panels
          v-model="selected"
          animated
          transition-prev="jump-up"
          transition-next="jump-up"
        >
          <q-tab-panel name="Relax Hotel">
            <div class="text-h4 q-mb-md">Welcome</div>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
          </q-tab-panel>

          <q-tab-panel name="Food">
            <div class="text-h4 q-mb-md">Food</div>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
          </q-tab-panel>

          <q-tab-panel name="Room service">
            <div class="text-h4 q-mb-md">Room service</div>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
          </q-tab-panel>

          <q-tab-panel name="Room view">
            <div class="text-h4 q-mb-md">Room view</div>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.</p>
          </q-tab-panel>
        </q-tab-panels>
      </template>
    </q-splitter>
  </div>


  <div class="q-pa-md">
    <q-card class="my-card">
      <q-video src="https://www.youtube.com/embed/k3_tw44QsZQ?rel=0" />

      <q-card-section>
        <div class="text-h6">Our Changing Planet</div>
        <div class="text-subtitle2">by John Doe</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
        eiusmod tempor incididunt ut labore et dolore magna aliqua.
      </q-card-section>
    </q-card>
  </div>

  <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card" flat bordered>
      <q-card-section horizontal>
        <q-card-section class="q-pt-xs">
          <div class="text-overline">Overline</div>
          <div class="text-h5 q-mt-sm q-mb-xs">Title</div>
          <div class="text-caption text-grey">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
          </div>
        </q-card-section>

        <q-card-section class="col-5 flex flex-center">
          <q-img
            class="rounded-borders"
            src="https://cdn.quasar.dev/img/parallax2.jpg"
          />
        </q-card-section>
      </q-card-section>

      <q-separator />

      <q-card-actions>
        <q-btn flat round icon="event" />
        <q-btn flat>
          7:30PM
        </q-btn>
        <q-btn flat color="primary">
          Reserve
        </q-btn>
      </q-card-actions>
    </q-card>

    <q-card class="my-card" flat bordered>
      <q-item>
        <q-item-section avatar>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/boy-avatar.png">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label>Title</q-item-label>
          <q-item-label caption>
            Subhead
          </q-item-label>
        </q-item-section>
      </q-item>

      <q-separator />

      <q-card-section horizontal>
        <q-card-section>
          {{ lorem }}
        </q-card-section>

        <q-separator vertical />

        <q-card-section class="col-4">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        </q-card-section>
      </q-card-section>
    </q-card>

    <q-card class="my-card">
      <q-card-section horizontal>
        <q-img
          class="col-5"
          src="https://cdn.quasar.dev/img/parallax1.jpg"
        />

        <q-card-section>
          {{ lorem }}
        </q-card-section>
      </q-card-section>

      <q-separator />

      <q-card-actions>
        <q-btn flat round icon="event" />
        <q-btn flat>
          5:30PM
        </q-btn>
        <q-btn flat>
          7:00PM
        </q-btn>
        <q-btn flat color="primary">
          Reserve
        </q-btn>
      </q-card-actions>
    </q-card>
  </div>

  
  <q-footer reveal elevated class="bg-dark -8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <div>Yovan Ramón Yaune Enovore &copy; 2023</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
</template>

<script>
import { ref } from 'vue'
import { useQuasar } from 'quasar'

export default {
  setup () {
    const $q = useQuasar()
    return {
      slide: ref('style'),
      lorem1: 'Hola1.',
      lorem2: 'Hola4.',
      lorem3: 'Hola3.',
      lorem4: 'Hola2.',
      drawerLeft: ref($q.screen.width > 700),
      drawerRight: ref($q.screen.width > 500),
      splitterModel: ref(50),
      selected: ref('Food'),
      simple: [
        {
          label: 'Relax Hotel',
          children: [
            {
              label: 'Food',
              icon: 'restaurant_menu'
            },
            {
              label: 'Room service',
              icon: 'room_service'
            },
            {
              label: 'Room view',
              icon: 'photo'
            }
          ]
        }
      ]
    }
  }
}

</script>
