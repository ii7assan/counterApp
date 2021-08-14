<template>
  <!-- <v-container fluid>
    <v-row justify="center" align="center">
      <v-col v-for="elevation in elevations" :key="elevation.id" cols="3">
        <v-sheet
          :elevation="elevation.id"
          class="mx-auto display-3 text-center pa-4"
          height="100"
          width="100"
        >
          {{ days | twoDigits }}
          {{ hours | twoDigits }}
        </v-sheet>
        <div class="mx-auto text-center">
          {{ elevation.time }}
        </div>
      </v-col>
    </v-row>
  </v-container> -->
  <div class="ma-5">
    <v-sheet
      class="mx-auto ma-9 display-3 text-center pa-4"
      height="100"
      width="100"
    >
      {{ displayDays }}
      DAY
    </v-sheet>

    <v-sheet
      class="mx-auto ma-9 display-3 text-center pa-4"
      height="100"
      width="100"
    >
      {{ displayHours }}
      HOUR
    </v-sheet>

    <v-sheet
      class="mx-auto ma-9 display-3 text-center pa-4"
      height="100"
      width="100"
    >
      {{ displayMinutes }}
      MIN
    </v-sheet>

    <v-sheet
      class="mx-auto display-3 text-center pa-4"
      height="100"
      width="100"
    >
      {{ displaySeconds }}
      SECONDS
    </v-sheet>
  </div>
</template>

<script>
export default {
  data: () => ({
    displayDays: 0,
    displayHours: 0,
    displayMinutes: 0,
    displaySeconds: 0,
    expired: false,
  }),
  props: {
    year: Number,
    month: Number,
    date: Number,
    minutes: Number,
    seconds: Number,
    milliseconds: Number,
  },
  computed: {
    _seconds: () => 1000,
    _minutes() {
      return this._seconds * 60;
    },
    _hours() {
      return this._minutes * 60;
    },
    _days() {
      return this._hours * 24;
    },
    // endTime() {
    //   return new Date(
    //     this.year,
    //     this.month,
    //     this.date,
    //     this.hour,
    //     this.minutes,
    //     this.seconds,
    //     this.milliseconds
    //   ).getTime();
    // },
  },
  mounted() {
    this.showRemaning();
    console.log(this.displayDays);
  },
  methods: {
    formatDate: (num) => (num < 10 ? "0" + num : num),
    showRemaning() {
      const timer = setInterval(() => {
        const now = new Date().getTime();
        const end = new Date(2021,10,1,4,5,4,4).getTime()
        const distance = end - now;

        if (distance < 0) {
          clearInterval(timer);
          this.expired = true;
          return;
        }

        const days = Math.floor(distance / this._days);
        const hours = Math.floor((distance % this._days) / this._hours);
        const minutes = Math.floor((distance % this._hours) / this._minutes);
        const seconds = Math.floor((distance % this._minutes) / this._seconds);
        this.displayMinutes = this.formatDate(minutes);
        this.displaySeconds = this.formatDate(seconds);
        this.displayHours = this.formatDate(hours);
        this.displayDays = this.formatDate(days);
      }, 1000);
    },
  },
};
</script>

<style>
</style>