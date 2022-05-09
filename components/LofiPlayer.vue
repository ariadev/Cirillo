<template>
  <div class="w-auto p-4 flex flex-col justify-between items-center h-full shadow-xl border rounded-xl">
    <div class="w-full flex justify-between h-full mb-4 items-center">
      <div class="w-12 h-12 bg-gray-100 flex justify-center items-center rounded-full text-center">
        <img src="~/assets/icons/left.svg" alt="left arrow">
      </div>

      <img class="inset-0 h-full w-20 object-cover rounded-full" src="~/assets/covers/lofi.webp" alt="lo-fi cover">

      <div class="w-12 h-12 bg-gray-100 flex justify-center items-center rounded-full text-center">
        <img src="~/assets/icons/right.svg" alt="left arrow">
      </div>
    </div>
    <div class="w-full">
      <audio controlsList="nodownload" class="w-full" controls :src="songUrl">
        Your browser does not support the
        <code>audio</code> element.
      </audio>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        songName: 'لوفی 17',
        songUrl: 'https://www.chosic.com/wp-content/uploads/2021/09/Morning-Routine-Lofi-Study-Music.mp3'
      }
    }
  }
</script>
<style>

</style>
