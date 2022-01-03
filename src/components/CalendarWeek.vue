<template>
  <div id="calender-week">
    <div class="card-group">
      <div class="card" v-for="i in 7" :key="i">
        <div class="card-header text-center" role="button">
          <strong>Montag</strong>
        </div>
        <div class="card-body">
          <CalendarDay />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CalendarDay from "./CalendarDay.vue";
export default {
  name: "CalendarWeek",
  components: { CalendarDay },
};
</script>

<style lang="sss" scoped></style>
