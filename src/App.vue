<template>
  <div class="container-fluid mt-5">
    <div class="row">
      <div class="col-12">
        <keep-alive>
          <transition name="fade" mode="out-in" appear>
            <component :is="activeView" />
          </transition>
        </keep-alive>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col-4 offset-4">
        <CalendarEntry />
      </div>
      <div class="col-2 offset-2">
        <div class="float-end">
          <!-- Mit dem Button blenden wir die Calendar-Settings-Component ein bzw. aus. -->
          <button
            class="btn btn-lg mb-2"
            :class="buttonSettingsClasses"
            @click="toggleDisplaySettings"
          >
            <i class="fas fa-cogs"></i>
          </button>
        </div>
        <transition name="fade">
          <CalendarSettings v-if="displaySettings" />
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Store from "./store";
import { defineAsyncComponent } from "vue";
import CalendarWeekAsList from "./components/CalendarWeekAsList.vue";
import CalendarWeek from "./components/CalendarWeek.vue";
import CalendarEntry from "./components/CalendarEntry.vue";
//import CalendarSettings from "./components/CalendarSettings.vue";
export default {
  name: "App",
  components: {
    CalendarWeek,
    CalendarEntry,
    CalendarWeekAsList,
    CalendarSettings: defineAsyncComponent(() => {
      return import(
        /*webpackChunkName: 'CalendarSettingsComponent'*/ "./components/CalendarSettings.vue"
      );
    }),
  },
  data() {
    return {
      displaySettings: false,
    };
  },
  methods: {
    toggleDisplaySettings() {
      this.displaySettings = !this.displaySettings;
    },
  },
  computed: {
    buttonSettingsClasses() {
      return this.displaySettings ? ["btn-success"] : ["btn-outline-success"];
    },
    activeView() {
      return Store.getters.activeView();
    },
  },
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.min.css";
@import "~@fortawesome/fontawesome-free/css/all.min.css";

.square {
  width: 40px;
  height: 40px;
}
/*Transition: Fade */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}
.fade-enter-active,
.fade-leave-active {
  transition: all 0.25s ease-out;
}
</style>
