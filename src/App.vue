<template>
  <div class="container-fluid mt-5">
    <div class="row">
      <div class="col-12">
        <CalendarWeek />
      </div>
    </div>
    <div class="row mt-3">
      <div class="col-4 offset-4">
        <CalendarEntry />
      </div>
      <div class="col-2 offset-2">
        <div class="float-end">
          <!-- Mit dem Button blenden wir die Calendar-Settings-Component ein bzw. aus. -->
          <button class="btn btn-lg mb-2">
            <i class="fas fa-cogs"></i>
          </button>
        </div>
        <!-- Anfang: Template für die Calendar-Settings-Component -->
        <div id="calendar-settings">
          <div class="card">
            <div class="card-header text-center bg-success text-white">
              <strong>Einstellungen</strong>
            </div>
            <div class="card-body">
              <ul class="nav nav-pills nav-fill">
                <li v-for="i in 2" :key="i" class="nav-item" role="button">
                  <a class="nav-link"
                    ><i class="fas fa-icons text-success"></i
                  ></a>
                </li>
              </ul>
              <hr />
              <ul class="nav nav-pills nav-fill">
                <li class="nav-item" role="button">
                  <a class="nav-link"
                    ><i class="fas fa-sort-numeric-down-alt text-success"></i
                  ></a>
                </li>
                <li class="nav-item" role="button">
                  <a class="nav-link"
                    ><i class="fas fa-sort-alpha-down text-success"></i
                  ></a>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <!-- Ende: Template für die Calendar-Day-Component -->
      </div>
    </div>
  </div>
</template>

<script>
import CalendarWeek from "./components/CalendarWeek.vue";
import CalendarEntry from "./components/CalendarEntry.vue";
export default {
  name: "App",
  components: {
    CalendarWeek,
    CalendarEntry,
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
</style>
