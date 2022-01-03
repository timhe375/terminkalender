<template>
  <div id="calendar-day">
    <!-- Anfang: Template für die Calendar-Event-Component -->
    <div id="calendar-event">
      <div class="alert text-center">
        <div>
          <strong>Hoch</strong>
        </div>

        <div>Vue.js 3 lernen</div>

        <div>
          <i class="fas fa-edit me-2" role="button"></i>
          <i class="far fa-trash-alt" role="button"></i>
        </div>
      </div>
    </div>
    <!-- Ende: Template für die Calendar-Event-Component -->
  </div>
</template>

<script>
export default {
  name: "CalendarDay",
};
</script>

<style scoped></style>
