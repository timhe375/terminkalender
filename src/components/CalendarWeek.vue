<template>
  <div id="calender-week">
    <div class="card-group"></div>
    <CalendarDay v-for="day in calendarWeekData" :key="day.id" :day="day" />
  </div>
</template>

<script>
import CalendarDay from "./CalendarDay.vue";
import Store from "../store";
export default {
  name: "CalendarWeek",
  components: { CalendarDay },
  data() {
    return {
      calendarWeekData: Store.state.calendarWeekData,
    };
  },
};
</script>

<style scoped></style>
