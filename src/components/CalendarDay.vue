<template>
  <div class="card borde-start" :class="cardClasses">
    <div
      class="card-header text-center"
      :class="cardHeaderClasses"
      role="button"
      @click="setActiveDay()"
    >
      <strong>{{ day.fullName }}</strong>
    </div>
    <div class="card-body">
      <transition name="fade" mode="out-in">
        <div v-if="day.events.length">
          <transition-group name="list">
            <CalendarEvent
              v-for="event in events"
              :key="event.title"
              :event="event"
              :day="day"
            >
              <template v-slot:eventPriority="slotProps"
                ><h5>{{ slotProps.priorityDisplayName }}</h5></template
              >
              <template v-slot="{ event }">
                <i>{{ event.title }}</i></template
              >
            </CalendarEvent>
          </transition-group>
        </div>
        <div v-else>
          <div class="alert alert-ligth text-center">
            Keine Termine für den Tag
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
import CalendarEvent from "./CalendarEvent.vue";
import Store from "../store";
export default {
  name: "CalendarDay",
  components: {
    CalendarEvent,
  },
  props: {
    day: {
      type: Object,
      required: true,
      default: function () {
        return {
          id: -1,
          fullName: "fehlender Wochentag",
          events: [],
        };
      },
    },
  },
  computed: {
    cardClasses() {
      return this.day.id == Store.getters.activeDay().id
        ? ["border-primary"]
        : null;
    },
    cardHeaderClasses() {
      return this.day.id == Store.getters.activeDay().id
        ? ["bg-primary", "text-white"]
        : null;
    },
    events() {
      return Store.getters.events(this.day.id);
    },
  },
  methods: {
    setActiveDay() {
      Store.mutations.setActiveDay(this.day.id);
    },
  },
};
</script>

<style scoped>
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
.list-enter-active,
.list-leave-active {
  transition: all 1s ease;
}
</style>
