<template>
  <div class="w-auto flex flex-col justify-center items-center h-full shadow-xl border rounded-xl">
    <span class="py-4">{{today}}</span>

    <div class="flex items-center py-3 h-full">
      <h3 class="text-5xl font-extrabold text-purple-600">{{hours}}:{{minutes}}:{{seconds}}</h3>
    </div>

    <div class="flex justify-between w-full items-end p-2 space-x-2 border-t">
      <div @click="finishStopWatch" class="py-4 text-sm w-1/3 rounded-lg bg-purple-900 text-white font-bold text-center center">
        اتمام مطالعه
      </div>

      <div @click="stopStopWatch" v-if="stop" class="py-4 text-sm w-2/3 bg-pink-400 text-white font-bold rounded-lg text-center center">
        توقف
      </div>

      <div @click="startStopWatch" v-else class="py-4 text-sm w-2/3 bg-purple-600 rounded-lg font-bold text-white text-center border-l border-r">
        شروع
      </div>
    </div>
  </div>
</template>
<script>
  import persianDate from 'persian-date';

  export default {
    data() {
      return {
        today: '',
        hours: '0' + 0,
        minutes: '0' + 0,
        seconds: '0' + 0,
        interval: null,
        stop: false,
      }
    },
    mounted() {
      const today = new persianDate().format('dddd, DD MMMM YYYY');
      this.today = today
    },
    methods: {
      startStopWatch() {
        this.stop = true
        clearInterval(this.interval);
        this.interval = setInterval(this.startTimer, 1000);
      },
      startTimer() {
        this.seconds++

        if(this.seconds <= 9){
          this.seconds = '0' + this.seconds;
        }

        if (this.seconds > 59) {
          this.minutes++;
          this.minutes = "0" + this.minutes;
          this.seconds = "0" + 0
        }

        if (this.minutes > 59) {
          this.hours++;
          this.hours = "0" + this.hours;
          this.minutes = "0" + 0;
          this.seconds = "0" + 0;
        }
      },
      stopStopWatch() {
        this.stop = false
        clearInterval(this.interval);
      },
      async finishStopWatch() {
        this.stop = false

        const data = {
          'persian_date': this.today,
          'hours': this.hours.toString(),
          'minutes': this.minutes.toString(),
          'seconds': this.seconds.toString(),
        };

        await this.$axios.$post('store', {...data}).then(response => {
          return alert(response.message);
        }).catch(err => {
          return alert(err);
        })

        clearInterval(this.interval);
        this.hours = '0' + 0
        this.minutes = '0' + 0
        this.seconds = '0' + 0
      }
    }
  }
</script>
<style>

</style>
