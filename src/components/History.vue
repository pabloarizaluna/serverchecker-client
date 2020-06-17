<template>
  <div class="container space-y-2 mx-auto px-4 py-4 bg-gray-200">
    <h1 class="text-gray-900 font-bold text-xl">Records</h1>
    <ul class="list-disc px-4">
      <li class="text-gray-700 text-base" v-for="record in dat.items" :key="record">
        <a
          class="font-bold text-sm text-blue-500 hover:text-blue-800"
          :href="'https://' + record"
        >{{ record }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "History",
  props: {
    dat: Object
  }
};
</script>

<style scoped>
</style>