<template>
  <div id="calendar-event">
    <div class="alert text-center" :class="alertColor">
      <div v-if="!event.edit">
        <div>
          <slot name="eventPriority" :priorityDisplayName="priorityDisplayName"
            ><strong>{{ priorityDisplayName }}</strong></slot
          >
          <!-- <strong>{{ priorityDisplayName }}</strong> -->
        </div>

        <!-- <div>{{ event.title }}</div> -->
        <slot :event="event"
          ><div>{{ event.title }}</div></slot
        >

        <div>
          <i class="fas fa-edit me-2" role="button" @click="editEvent"></i>
          <i class="far fa-trash-alt" role="button" @click="deleteEvent"></i>
        </div>
      </div>
      <div v-else>
        <p>Kein Event</p>
      </div>
    </div>
  </div>
</template>

<script>
import Store from "../store";
export default {
  name: "CalendarEvent",
  props: {
    event: Object,
    day: Object,
  },
  computed: {
    priorityDisplayName() {
      switch (this.event.priority) {
        case 1:
          return "Tief";
        case 0:
          return "Mittel";
        case -1:
          return "Hoch";
      }
      return "Unbekannte Priorität";
    },
    alertColor() {
      return "alert-" + this.event.color;
    },
  },
  methods: {
    deleteEvent() {
      Store.mutations.deleteEvent(this.day.id, this.event.title);
    },
    editEvent() {
      Store.mutations.editEvent(this.day.id, this.event.title);
    },
  },
};
</script>

<style></style>
