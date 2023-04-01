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
            color="positive"
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
        <q-carousel-slide name="sabiasQue1" class="column no-wrap flex-center">
          <h1 class="text-h6">Sabias que?</h1>
          {{ sabiasQue1 }}
        </q-carousel-slide>
        <q-carousel-slide name="sabiasQue2" class="column no-wrap flex-center">
          <h1 class="text-h6">Sabias que?</h1>
          {{ sabiasQue2 }}
        </q-carousel-slide>
        <q-carousel-slide name="sabiasQue3" class="column no-wrap flex-center">
          <h1 class="text-h6">Sabias que?</h1>
          {{ sabiasQue3 }}
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
      sabiasQue1:
        "La realidad virtual y la realidad aumentada seguirán siendo tendencias importantes en la industria del entretenimiento y en la educación.",
      sabiasQue2:
        "La automatización de procesos y el uso de chatbots se incrementará en diferentes ámbitos empresariales para optimizar la atención al cliente.",
      sabiasQue3:
        "La ciberseguridad se convertirá en una prioridad aún mayor para las empresas, a medida que los riesgos de ciberataques sigan en aumento.",
      sabiasQue4:
        "La inteligencia artificial y el aprendizaje automático serán cada vez más utilizados en aplicaciones empresariales.",
      sabiasQue5:
        "El internet de las cosas (IoT) se expandirá aún más, abriendo nuevas oportunidades de negocio.",
      sabiasQue6:
        "La tecnología blockchain seguirá siendo una tendencia importante en la seguridad y la gestión de datos.",

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
