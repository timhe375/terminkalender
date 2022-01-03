<template>
  <div id="calendar-day">
    <CalendarEvent />
  </div>
</template>

<script>
import CalendarEvent from "./CalendarEvent.vue";
export default {
  name: "CalendarDay",
  components: {
    CalendarEvent,
  },
};
</script>

<style scoped></style>
