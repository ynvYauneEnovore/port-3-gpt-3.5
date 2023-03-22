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
        <div class="text-h6">Mi enfoque se basa en la combinación de habilidades creativas y técnicas, para lograr un resultado impresionante y funcional. Ya sea que se trate de diseño gráfico, desarrollo web o ambas cosas, me aseguro de que el resultado final sea de la más alta calidad.</div>
        <div class="text-subtitle2">by Yovam Yaune</div>
        <q-avatar rounded>
          <img src="https://cdn.quasar.dev/img/chaosmonkey.png">
        </q-avatar>
      </q-card-section>
    </q-card>

    <q-layout view="lHh Lpr lFf" container style="height: 400px" class="shadow-2 rounded-borders">
      <q-header reveal elevated>
        <q-toolbar>
          <q-btn flat round dense icon="menu" @click="drawerLeft = !drawerLeft" />

          <q-toolbar-title>
            <strong>Quasar</strong> Framework
          </q-toolbar-title>

          <q-btn flat round dense icon="menu" @click="drawerRight = !drawerRight" />
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawerLeft"
        :width="150"
        :breakpoint="700"
        behavior="desktop"
        bordered
        class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <div class="q-pa-sm">
            <div v-for="n in 50" :key="n">Drawer {{ n }} / 50</div>
          </div>
        </q-scroll-area>
      </q-drawer>

      <q-drawer
        side="right"
        v-model="drawerRight"
        bordered
        :width="150"
        :breakpoint="500"
        behavior="desktop"
        class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <div class="q-pa-sm">
            <div v-for="n in 50" :key="n">Drawer {{ n }} / 50</div>
          </div>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <q-page padding style="padding-top: 66px">
          <p v-for="n in 15" :key="n">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit nihil praesentium molestias a adipisci, dolore vitae odit, quidem consequatur optio voluptates asperiores pariatur eos numquam rerum delectus commodi perferendis voluptate?
          </p>
          <div class="q-pa-md q-gutter-md">
    <div class="row justify-center">
      <div class="row items-center q-gutter-x-sm">
        <q-radio v-model="targetEl" :val="false" label="false (no target whatsoever)" />
        <q-radio v-model="targetEl" :val="true" label="true (original parent)" />
        <q-radio v-model="targetEl" val="#target-img-1" label="#target-img-1" />
        <q-radio v-model="targetEl" val="#target-img-2" label="#target-img-2" />
        <q-radio v-model="targetEl" val="#bogus" label="#bogus" />
      </div>
    </div>
    <div class="row justify-center">
      <q-img src="https://cdn.quasar.dev/img/material.png" id="target-img-1" style="height: 100px">
        <div class="absolute-bottom-right" style="border-top-left-radius: 5px">#target-img-1</div>
      </q-img>
      <q-img src="https://cdn.quasar.dev/img/parallax2.jpg" id="target-img-2" style="height: 100px">
        <div class="absolute-bottom-right" style="border-top-left-radius: 5px">#target-img-2</div>
      </q-img>
      <q-img src="https://cdn.quasar.dev/img/blueish.jpg" style="height: 100px">
        <div class="absolute-bottom-right" style="border-top-left-radius: 5px">Original parent</div>
        <q-menu touch-position :target="targetEl">
          <q-list>
            <q-item
              v-for="n in 5"
              :key="n"
              v-close-popup
              clickable
            >
              <q-item-section>Label</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-img>
    </div>
  </div>


          <!-- place QPageSticky at end of page -->
          <q-page-sticky expand position="top">
            <q-toolbar class="bg-accent text-white">
              <q-avatar>
                <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
              </q-avatar>
              <q-toolbar-title>
                Articulo [Yovan Ramón Yaune Enovore]
              </q-toolbar-title>
            </q-toolbar>
          </q-page-sticky>
        </q-page>
      </q-page-container>
    </q-layout>
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
        <img src="img/yovan-1.png">
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
          <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" style="width: 150px; height: 150px">
          <div class="text-h3 text-white text-center">Quasar Framework</div>
          <div class="text-h6 text-grey-3 text-center">
            v{{ $q.version }}
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
