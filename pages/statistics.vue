<template>
  <div dir="rtl" class="container pb-24 px-4 pt-4 pb-24">

    <h3 class="mb-3">لیست ساعت های مطالعه شما:</h3>

    <div v-if="!timers" class="flex justify-between p-2 rounded border mb-2">

      <span>در حال بارگزاری...</span>

    </div>

    <div v-for="timer of timers">

      <div class="flex justify-between p-3 rounded-lg border mb-2" :id="timer.id">

        <span>{{timer.date}}</span>

        <span>{{timer.hours}}:{{timer.minutes}}:{{timer.seconds}}</span>

      </div>
    </div>
  </div>
</template>
<script>
  export default {
    async asyncData({ $axios }) {
      const timers = await $axios.$get('all')
      return { timers }
    }
  }
</script>
<style>

</style>
