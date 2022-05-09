<template>
  <div class="">
    <Nuxt />

    <div class="container mx-auto fixed bottom-0">
      <BottomNavigation />
    </div>
  </div>
</template>
<script>
  import BottomNavigation from "../components/BottomNavigation";

  export default {
    components: {BottomNavigation},
    layout: 'default',
  }
</script>
<style>

</style>
