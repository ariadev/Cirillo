<template>
  <div class="border bg-gray-100 flex justify-between px-4">
    <div v-for="route of routes">
      <div class="py-4 my-2 px-7" :key="route.id">
        <nuxt-link :to="route.url">{{route.name}}</nuxt-link>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        routes: [
          {id: 0, name: "لوفی", url: "/lofi"},
          {id: 1, name: "تایمر", url: "/"},
          {id: 2, name: "آمار", url: "/statistics"},
        ]
      }
    }
  }
</script>
<style>
  a.nuxt-link-exact-active {
    font-weight: bold;
  }
</style>
