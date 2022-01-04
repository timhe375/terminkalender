<template>
  <div class="card">
    <div class="card-header text-center" role="button">
      <strong>{{ day.fullName }}</strong>
    </div>
    <div class="card-body">
      <CalendarEvent />
    </div>
  </div>
</template>

<script>
import CalendarEvent from "./CalendarEvent.vue";
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
};
</script>

<style scoped></style>
