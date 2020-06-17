<template>
  <div class="container space-y-4 mx-auto px-4 py-4 bg-gray-200">
    <div class="flex space-x-4">
      <img :src="dat.logo" class="h-8 w-8 md:flex-shrink-0" alt="Host Logo" />
      <h1 class="text-gray-900 font-bold text-xl">{{ dat.title }}</h1>
    </div>
    <p class="text-gray-700 text-base">
      SSL Grade: {{ dat.ssl_grade }}
      <br />
      <template v-if="dat.servers_changed">
        Previous SSL Grade: {{ dat.previous_ssl_grade }}
        <br />
      </template>
      Is Down: {{ dat.is_down }}
      <br />Link:
      <a
        class="font-bold text-sm text-blue-500 hover:text-blue-800"
        :href="'https://' + dat.host"
      >{{ dat.host }}</a>
    </p>
    <Server :servers="dat.servers"></Server>
  </div>
</template>

<script>
import Server from "./Server.vue";

export default {
  name: "Host",
  components: {
    Server
  },
  props: {
    dat: Object
  }
};
</script>

<style scoped>
</style>