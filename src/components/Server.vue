<template>
  <div>
    <h2 class="text-lg text-gray-900 font-bold">Servers</h2>
    <table class="table-fixed">
      <thead>
        <tr>
          <th class="px-4 py-2">Address</th>
          <th class="px-4 py-2">SSL Grade</th>
          <th class="px-4 py-2">Country</th>
          <th class="px-4 py-2">Owner</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(server, index) in servers" :key="index">
          <td class="border px-4 py-2">{{ server.address }}</td>
          <td class="border px-4 py-2">{{ server.ssl_grade }}</td>
          <td class="border px-4 py-2">{{ server.country }}</td>
          <td class="border px-4 py-2">{{ server.owner }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>>

<script>
export default {
  name: "Server",
  props: {
    servers: Array
  }
};
</script>

<style scoped>
</style>