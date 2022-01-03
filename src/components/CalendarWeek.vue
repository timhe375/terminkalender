<template>
  <div id="calender-week">
    <div class="card-group"></div>
    <CalendarDay v-for="i in 7" :key="i" />
  </div>
</template>

<script>
import CalendarDay from "./CalendarDay.vue";
export default {
  name: "CalendarWeek",
  components: { CalendarDay },
};
</script>

<style scoped></style>
