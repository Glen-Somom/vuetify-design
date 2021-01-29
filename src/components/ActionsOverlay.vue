<template>
  <v-alert elevation="5" :class="isMobile ? 'mobileOverlay': 'overlay'">
    <v-row align="center" justify="space-between" class="pa-3">
      <div>
        <v-btn
            color="black"
            text
            tile
            elevation="0"
        >
          Save
        </v-btn>
        <v-menu offset-y>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
                color="white"
                elevation="0"
                tile
                v-bind="attrs"
                v-on="on"
                min-width="10"
                width="10"
            >
              <v-icon>mdi-chevron-down</v-icon>
            </v-btn>
          </template>
          <v-list class="pa-2">
            <v-list-item @click="dummyClick">
              Cancel
            </v-list-item>
          </v-list>
        </v-menu>
      </div>

      <div>

        <v-btn
            color="orange darken-2"
            tile
            dark
            elevation="0"
        >
          Approve
        </v-btn>
        <v-menu :close-on-content-click="false" offset-x>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
                color="orange darken-2"
                tile
                dark
                elevation="0"
                v-bind="attrs"
                v-on="on"
                min-width="10"
                width="10"
            >
              <v-icon>mdi-chevron-down</v-icon>
            </v-btn>
          </template>
          <v-list class="pa-2">
            <v-list-item>
              <v-checkbox
                  v-model="approve.email"
                  label="Email"
              ></v-checkbox>
            </v-list-item>
            <v-list-item>
              <v-checkbox
                  v-model="approve.download"
                  label="Download"
              ></v-checkbox>
            </v-list-item>
            <v-list-item>
              <v-checkbox
                  v-model="approve.request"
                  label="Request Approval"
              ></v-checkbox>
            </v-list-item>
          </v-list>
        </v-menu>
      </div>

    </v-row>
  </v-alert>
</template>
<script>
import {defineComponent, reactive, computed, watch} from "@vue/composition-api";

export default defineComponent({
  setup(props, {root}) {
    const isMobile = computed(() => root.$vuetify.breakpoint.mobile);
    const approve = reactive({email: false, download: false, request: false});

    watch(() => root.$vuetify.breakpoint.mobile, (bp) => {
      console.log(bp);
    })

    function dummyClick() {

    }


    return {approve, isMobile, dummyClick};
  }
})
</script>
<style scoped>
.overlay {
  z-index: 3;
  position: fixed;
  bottom: 10px;
  width: 50vw;
}
.mobileOverlay{
  z-index: 3;
  position: fixed;
  bottom: 0;
  width: 100vw;
}
</style>
