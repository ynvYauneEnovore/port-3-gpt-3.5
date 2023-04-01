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
              <q-btn dense flat icon="close" close>
                <q-tooltip class="bg-white text-primary">Close</q-tooltip>
              </q-btn>
              <div class="text-h6 q-mb-md">Información</div>
              <q-toggle
                color="positive"
                v-model="mobileData"
                label="Dark"
                disable
              />
              <q-toggle v-model="bluetooth" label="Bluetooth" disable />
              <br /><q-separator inset /><br />
              <q-toggle v-model="bluetooth" label="En desarrollo" disable />
              <br /><q-separator inset /><br />
              chatBot
              <q-btn
                padding="xs lg"
                color="positive"
                round
                @click="bar2 = true"
              >
                <q-spinner-comment color="dark" size="2em" />
                <q-icon color="dark" size="4em" name="smart_toy"></q-icon>
              </q-btn>
              <q-dialog
                v-model="bar2"
                persistent
                transition-show="flip-down"
                transition-hide="flip-up"
              >
                <q-card class="bg-primary text-white">
                  <q-bar>
                    <q-icon name="network_wifi" />
                    <q-icon name="network_cell" />
                    <q-icon name="battery_full" />

                    <q-space />

                    <q-btn dense flat icon="close" close>
                      <q-tooltip class="bg-white text-primary">Close</q-tooltip>
                    </q-btn>
                  </q-bar>

                  <q-card-section>
                    <div class="text-h6">
                      Quieres que te avise cuando el sistema chatBot este
                      completemente integrado en mi web. Por ahora el modelo
                      esta en desarrollo esta funcionando solo para los dev. si
                      quieres realizr test avisame por este medio.

                      <form @submit.prevent="simulateSubmit" class="q-pa-md">
                        <!-- a simple text field watching for the enter key release -->
                        <q-input
                          filled
                          color="teal"
                          hint="Type then hit Enter key above"
                          v-model="test"
                        />

                        <!--
      A button with v-model set to submit.
      v-model scope variable must be a strict Boolean
    -->
                        <div class="row justify-end">
                          <q-btn
                            type="submit"
                            :loading="submitting"
                            label="Save"
                            class="q-mt-md"
                            color="teal"
                          >
                            <template v-slot:loading>
                              <q-spinner-facebook />
                            </template>
                          </q-btn>
                        </div>
                      </form>
                    </div>
                  </q-card-section>
                </q-card>
              </q-dialog>
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

              <q-toggle v-model="activo" label="activo" />
              <br /><q-separator inset /><br />

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
            <q-fab-action @click="call" color="dark">
              <q-icon name="build"></q-icon>
            </q-fab-action>

            <q-fab-action @click="onClick" color="dark">
              <q-icon name="add_ic_call"></q-icon>
            </q-fab-action>

            <q-fab-action @click="seamless = true" color="dark">
              <q-icon name="interests"></q-icon>
            </q-fab-action>

            <q-fab-action @click="onClick" color="dark">
              <q-icon name="facebook"></q-icon>
            </q-fab-action>

            <q-fab-action @click="onClick" color="dark">
              <q-icon name="mail"></q-icon>
            </q-fab-action>
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
import { defineComponent, ref } from "vue";
import { useQuasar } from "quasar";
import { watch } from "vue";

export default defineComponent({
  methods: {
    IP_YNV() {
      window.location.href = "https://ynv-servis.tech";
    },
  },

  name: "MainLayout",

  setup() {
    const $q = useQuasar();
    const leftDrawerOpen = ref(false);
    const test = ref("");
    const submitting = ref(false);

    function simulateSubmit() {
      submitting.value = true;
      // Simulating a delay here.
      // When we are done, we reset "submitting"
      // Boolean to false to restore the
      // initial state.
      setTimeout(() => {
        // delay simulated, we are done,
        // now restoring submit to its initial state
        submitting.value = false;
      }, 3000);
    }

    watch(
      () => $q.dark.isActive,
      (val) => {
        console.log(val ? "On dark mode" : "On light mode");
      }
    );

    return {
      test,
      submitting,
      simulateSubmit,
      bar2: ref(false),
      seamless: ref(false),
      persistent: ref(false),
      onClick() {
        console.log("Clicked on a fab action");
      },
      call() {
        alert("Clicked on a fab action");
      },
      activo: ref(true),
      endesarrollo: ref(false),
      mobileData: ref(false),
      bluetooth: ref(false),
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
