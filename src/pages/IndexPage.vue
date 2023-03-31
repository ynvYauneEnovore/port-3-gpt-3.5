<template>
  <div class="row">
    <div class="col-md-9 col-12">
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
          <q-btn
            v-if="active"
            size="lg"
            icon="home"
            color="yellow"
            flat
            round
            dense
            @click="onClick"
          />
          <q-btn
            v-else
            size="sm"
            :icon="btnProps.icon"
            color="white"
            flat
            round
            dense
            @click="onClick"
          />
        </template>

        <q-carousel-slide name="style" class="column no-wrap flex-center">
          <img src="img/logo.png" :height="270" />
          <div class="q-mt-md text-center"></div>
        </q-carousel-slide>
        <q-carousel-slide name="tv" class="column no-wrap flex-center">
          <img src="img/v.png" :height="120" />
          La IA se ha convertido en una de las principales tendencias
          tecnológicas de los últimos años. * Las empresas están utilizando cada
          vez más asistentes virtuales impulsados por IA, como Siri de Apple,
          Google Assistant y Alexa de Amazon, para mejorar la interacción con
          sus clientes. Estos asistentes virtuales pueden ser utilizados para
          responder preguntas frecuentes, ofrecer recomendaciones personalizadas
          y mejorar la experiencia del usuario en general.
          <div class="q-mt-md text-center"></div>
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
    <div class="col-md-3 col-12">
      <q-card class="my-card" flat bordered>
        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="img/perf.png" />
            </q-avatar>
          </q-item-section>

          <q-item-section>
            <q-item-label>Desarrollador:</q-item-label>
            <q-item-label caption> @ramonenovore </q-item-label>
          </q-item-section>
        </q-item>

        <q-separator />

        <q-card-section horizontal>
          <q-card-section>
            {{ lorem }}
          </q-card-section>

          <q-separator vertical />

          <q-card-section class="col">
            "Soy un desarrollador de software creativo y enfocado en los
            detalles, con una sólida formación técnica y experiencia en la
            creación de soluciones tecnológicas para una variedad de necesidades
            empresariales."
          </q-card-section>
        </q-card-section>
      </q-card>
    </div>
  </div>
  <q-page class="">
    <div class="q-pa-md">
      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card" flat bordered>
          <q-img src="https://cdn.quasar.dev/img/parallax2.jpg" />

          <q-card-section>
            <div class="text-overline text-orange-9">Overline</div>
            <div class="text-h5 q-mt-sm q-mb-xs">Title</div>
            <div class="text-caption text-grey">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
              eiusmod tempor incididunt ut labore et dolore magna aliqua.
            </div>
          </q-card-section>

          <q-card-actions>
            <q-btn flat color="dark" label="Share" />
            <q-btn flat color="primary" label="Book" />

            <q-space />

            <q-btn
              color="grey"
              round
              flat
              dense
              :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
              @click="expanded = !expanded"
            />
          </q-card-actions>

          <q-slide-transition>
            <div v-show="expanded">
              <q-separator />
              <q-card-section class="text-subitle2">
                {{ lorem1 }}
              </q-card-section>
            </div>
          </q-slide-transition>
        </q-card>

        <q-card class="my-card">
          <q-parallax src="img/yovan-1.png" :height="150" />

          <q-card-section>
            <div class="text-h6">
              Mi enfoque se basa en la combinación de habilidades creativas y
              técnicas, para lograr un resultado impresionante y funcional. Ya
              sea que se trate de diseño gráfico, desarrollo web o ambas cosas,
              me aseguro de que el resultado final sea de la más alta calidad.
            </div>
            <div class="text-subtitle2">by Yovam Yaune</div>
            <q-avatar rounded>
              <img src="https://cdn.quasar.dev/img/chaosmonkey.png" />
            </q-avatar>
          </q-card-section>
        </q-card>
      </div>

      <q-video
        :ratio="16 / 9"
        src="https://www.youtube.com/embed/ml-npkj_LxM"
      />
    </div>
  </q-page>

  <div class="q-pa-md">
    <q-parallax>
      <template v-slot:media>
        <img src="img/card-3.png" />
      </template>

      <template v-slot:content="scope">
        <div
          class="absolute column items-center"
          :style="{
            opacity: 0.45 + (1 - scope.percentScrolled) * 0.55,
            top: scope.percentScrolled * 60 + '%',
            left: 0,
            right: 0,
          }"
        >
          <img src="img/v.png" style="width: 150px; height: 150px" />
          <div class="text-h3 text-white text-center">
            Portafolio - Personal - Yovan
          </div>
          <div class="text-h6 text-grey-3 text-center">v3.0.4</div>
        </div>
      </template>
    </q-parallax>
  </div>

  <div>
    <q-splitter v-model="splitterModel" style="height: 400px">
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
          <q-tab-panel name="Habilidades">
            <div class="text-h4 q-mb-md">Habilidades</div>

            <div class="relative-position">
              <div class="example-area q-pa-lg scroll">
                <div class="example-filler" />

                <q-list>
                  <q-item
                    v-for="n in 5"
                    :key="n"
                    :data-id="n"
                    class="q-my-md q-pa-sm bg-grey-3"
                    v-intersection="onIntersection"
                  >
                    <q-item-section
                      class="text-center"
                      style="background: #eee"
                    >
                      Item #{{ n }}
                    </q-item-section>
                    <q-item-section
                      class="text-center"
                      style="background: #eee"
                    >
                      Item #{{ n }}
                    </q-item-section>
                    <q-item-section
                      class="text-center"
                      style="background: #eee"
                    >
                      Item #{{ n }}
                    </q-item-section>
                  </q-item>
                </q-list>

                <div class="example-filler" />
              </div>

              <div
                class="example-state bg-primary text-white overflow-hidden rounded-borders text-center absolute-top-left q-ma-md q-pa-sm"
              >
                <transition-group
                  v-if="inView.length > 0"
                  name="in-view"
                  tag="ul"
                >
                  <li v-for="i in inView" :key="i" class="in-view-item">
                    {{ i }}
                  </li>
                </transition-group>
              </div>
            </div>
          </q-tab-panel>

          <q-tab-panel name="Códigos">
            <div class="text-h4 q-mb-md">Códigos</div>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
              praesentium cumque magnam odio iure quidem, quod illum numquam
              possimus obcaecati commodi minima assumenda consectetur culpa fuga
              nulla ullam. In, libero.
            </p>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
              praesentium cumque magnam odio iure quidem, quod illum numquam
              possimus obcaecati commodi minima assumenda consectetur culpa fuga
              nulla ullam. In, libero.
            </p>
          </q-tab-panel>

          <q-tab-panel name="Fraemworks">
            <div class="text-h4 q-mb-md">Fraemworks</div>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
              praesentium cumque magnam odio iure quidem, quod illum numquam
              possimus obcaecati commodi minima assumenda consectetur culpa fuga
              nulla ullam. In, libero.
            </p>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
              praesentium cumque magnam odio iure quidem, quod illum numquam
              possimus obcaecati commodi minima assumenda consectetur culpa fuga
              nulla ullam. In, libero.
            </p>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
              praesentium cumque magnam odio iure quidem, quod illum numquam
              possimus obcaecati commodi minima assumenda consectetur culpa fuga
              nulla ullam. In, libero.
            </p>
          </q-tab-panel>

          <q-tab-panel name="Librerías">
            <div class="text-h4 q-mb-md">Librerías</div>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
              praesentium cumque magnam odio iure quidem, quod illum numquam
              possimus obcaecati commodi minima assumenda consectetur culpa fuga
              nulla ullam. In, libero.
            </p>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quis
              praesentium cumque magnam odio iure quidem, quod illum numquam
              possimus obcaecati commodi minima assumenda consectetur culpa fuga
              nulla ullam. In, libero.
            </p>
          </q-tab-panel>
        </q-tab-panels>
      </template>
    </q-splitter>
  </div>

  <q-footer
    reveal
    elevated
    class="-2 text-white"
    style="background-color: rgba(1, 31, 43, 0.81)"
  >
    <q-toolbar>
      <q-toolbar-title>
        <div class="text-subtitle1">Yovan Ramón Yaune Enovore &copy; 2023</div>
      </q-toolbar-title>
    </q-toolbar>
  </q-footer>
</template>

<script>
import { ref } from "vue";
import { useQuasar } from "quasar";

export default {
  setup() {
    const $q = useQuasar();
    const inView = ref([]);

    function onIntersection(entry) {
      if (entry.isIntersecting === true) {
        add(entry.target.dataset.id);
      } else {
        remove(entry.target.dataset.id);
      }
    }
    function add(i) {
      remove(i);
      inView.value.push(i);
      inView.value.sort(sortAtoi);
    }
    function remove(i) {
      let index;
      while ((index = inView.value.indexOf(i)) > -1) {
        inView.value.splice(index, 1);
        inView.value.sort(sortAtoi);
      }
    }
    function sortAtoi(a, b) {
      return Number(a) - Number(b);
    }

    return {
      expanded: ref(false),
      slide: ref("style"),
      lorem1: "Hola1.",
      lorem2: "Hola4.",
      lorem3: "Hola3.",
      lorem4: "Hola2.",
      drawerLeft: ref($q.screen.width > 700),
      drawerRight: ref($q.screen.width > 500),
      splitterModel: ref(50),
      selected: ref("Food"),
      simple: [
        {
          label: "Habilidades",
          children: [
            {
              label: "Códigos",
              icon: "code",
            },
            {
              label: "Fraemworks",
              icon: "work",
            },
            {
              label: "Librerías",
              icon: "book",
            },
          ],
        },
      ],
      inView,
      onIntersection,
    };
  },
};
</script>
<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 350px


.example-area
  height: 300px
.example-filler
  height: 350px
.in-view-item
  transition: all 0.3s
  display: block
.in-view-enter, .in-view-leave-to
  opacity: 0
  transform: translateX(-30px)
.in-view-leave-active
  position: absolute
</style>
