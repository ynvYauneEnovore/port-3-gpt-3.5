<template>
  <q-layout view="lHh Lpr lFf">
    <q-header style="background-color: rgba(1, 31, 43, 0.81)">
      <q-toolbar>
        <q-toolbar-title>
          <h1 class="text-h5">
            <q-spinner-grid color="teal"></q-spinner-grid> Ideas en Acción
          </h1>
        </q-toolbar-title>

        <q-btn-dropdown class="glossy" label="DEV">
          <div class="row no-wrap q-pa-md">
            <div class="column">
              <div class="text-h6 q-mb-md">Información</div>
              <q-toggle
                color="positive"
                v-model="mobileData"
                label="Disponible"
              />
              <q-toggle v-model="bluetooth" label="Bluetooth" />
              <br /><q-separator inset /><br />

              <q-btn padding="xs lg" color="positive" round>
                <q-spinner-comment color="dark" size="2em" />
                <q-icon color="dark" size="4em" name="smart_toy"></q-icon>
              </q-btn>
            </div>

            <q-separator vertical inset class="q-mx-lg" />

            <div class="column items-center">
              <q-avatar size="72px">
                <img src="img/perf.png" />
              </q-avatar>

              <div class="text-subtitle1 q-mt-md q-mb-xs">
                Yovan Ramón Yaune Enovore
              </div>
              <br />

              <q-btn color="positive" @click="persistent = true">
                ir \ system<q-spinner-gears color="dark" size="2.5em" />
              </q-btn>

              <q-dialog
                v-model="persistent"
                persistent
                transition-show="scale"
                transition-hide="scale"
              >
                <q-card class="bg-teal text-white" style="width: 300px">
                  <q-card-section>
                    <div class="text-h6">Acceder al sistema de principal</div>
                  </q-card-section>

                  <q-card-section class="q-pt-none">
                    Mi sistema principal es un espacio privado y seguro donde
                    almaceno y gestiono todos mis recursos digitales y sistemas.
                    Cuenta con medidas avanzadas de seguridad y está diseñado
                    para ser escalable y confiable. Esto me permite acceder a
                    mis archivos y recursos de manera eficiente y protegerlos de
                    posibles amenazas externas.
                  </q-card-section>

                  <q-card-section class="q-pt-none">
                    (Haga click/toque en ATRAS para salir. )
                  </q-card-section>

                  <q-card-actions align="right" class="bg-white text-teal">
                    <q-btn
                      color="positive"
                      flat
                      label="ir"
                      v-close-popup
                      @click="IP_YNV"
                    />
                    <q-btn color="negative" flat label="Atras" v-close-popup />
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
            style="background-color: rgba(1, 31, 43, 0.81)"
          >
            <q-fab-action @click="onClick" color="dark">
              <q-icon name="build"></q-icon>
            </q-fab-action>

            <q-fab-action @click="onClick" color="dark">
              <q-icon name="add_ic_call"></q-icon>
            </q-fab-action>

            <q-fab-action @click="seamless = true" color="dark">
              <q-icon name="interests"></q-icon>
            </q-fab-action>

            <q-fab-action @click="onClick" color="dark">
              <q-icon name="build"></q-icon>
            </q-fab-action>

            <q-fab-action @click="onClick" color="dark">
              <q-icon name="facebook"></q-icon>
            </q-fab-action>
          </q-fab>
        </q-page-sticky>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>

  <div class="q-pa-md q-gutter-sm">
    <q-btn label="Click Me" color="primary" @click="seamless = true" />

    <q-dialog v-model="seamless" seamless position="bottom">
      <q-card style="width: 350px">
        <q-card-section class="row items-center no-wrap">
          <div>
            <div class="text-weight-bold">Redes Sociales</div>
            <div class="text-grey">@ramonenovore</div>
            <div class="q-pa-md">
              <q-btn-group spread>
                <q-btn color="purple" label="First" icon="timeline" />
                <q-btn color="purple" label="Second" icon="visibility" />
                <q-btn color="purple" label="Second" icon="visibility" />
                <q-btn color="purple" label="Second" icon="visibility" />
                <q-btn color="purple" label="Second" icon="visibility" />
              </q-btn-group>
            </div>
          </div>

          <q-space />

          <q-btn flat round icon="close" v-close-popup />
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>

  <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card">
      <q-card-section>
        {{ lorem }}
      </q-card-section>
    </q-card>

    <q-card
      class="my-card text-white"
      style="background: radial-gradient(circle, #35a2ff 0%, #014a88 100%)"
    >
      <q-card-section>
        <div class="text-h6">Our Changing Planet</div>
        <div class="text-subtitle2">by John Doe</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        {{ lorem }}
      </q-card-section>
    </q-card>

    <q-card dark bordered class="bg-grey-9 my-card">
      <q-card-section>
        <div class="text-h6">Our Changing Planet</div>
        <div class="text-subtitle2">by John Doe</div>
      </q-card-section>

      <q-separator dark inset />

      <q-card-section>
        {{ lorem }}
      </q-card-section>
    </q-card>

    <q-card flat bordered class="my-card">
      <q-card-section>
        <div class="text-h6">Our Changing Planet</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua.
      </q-card-section>

      <q-separator inset />

      <q-card-section>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua.
      </q-card-section>
    </q-card>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useQuasar } from "quasar";
import { watch } from "vue";

export default defineComponent({
  methods: {
    IP_YNV() {
      window.location.href = "http://192.168.1.1";
    },
  },

  name: "MainLayout",

  setup() {
    const $q = useQuasar();
    const leftDrawerOpen = ref(false);

    watch(
      () => $q.dark.isActive,
      (val) => {
        console.log(val ? "On dark mode" : "On light mode");
      }
    );

    return {
      seamless: ref(false),
      persistent: ref(false),
      onClick() {
        console.log("Clicked on a fab action");
      },
      mobileData: ref(true),
      bluetooth: ref(true),
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
