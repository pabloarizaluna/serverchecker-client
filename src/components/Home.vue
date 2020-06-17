<template>
  <div class="space-y-2">
    <div class="flex justify-around mx-auto lg:mt-6">
      <img class="h-32 w-32 lg:h-64 lg:w-64" alt="SSL Checker logo" src="../assets/logo.png" />
    </div>
    <div class="flex flex-col bg-gray-200 w-full max-w-lg mx-auto">
      <div class="bg-gray-400 px-4 py-2 m-1">
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          type="url"
          placeholder="example.com"
          v-model="url"
          @keypress.enter="search()"
        />
      </div>
      <div class="flex items-center justify-around bg-gray-400 px-4 py-2 m-1">
        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="button"
          @click.prevent="search()"
        >Search</button>

        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          @click.prevent="record()"
        >Historic</button>
      </div>
    </div>
    <template v-if="searched">
      <Host :dat="result"></Host>
    </template>
    <template v-if="recorded">
      <History :dat="records"></History>
    </template>
    <p class="container text-center text-gray-600 mx-auto px-4 py-4">
      Icons made by
      <a
        class="font-bold text-sm text-blue-300 hover:text-blue-500"
        href="https://www.flaticon.com/authors/becris"
        title="Becris"
      >Becris</a> from
      <a
        class="font-bold text-sm text-blue-300 hover:text-blue-500"
        href="https://www.flaticon.com/"
        title="Flaticon"
      >www.flaticon.com</a>
    </p>
  </div>
</template>>

<script>
import Host from "./Host.vue";
import History from "./History";

export default {
  name: "Home",
  components: {
    Host,
    History
  },
  data: function() {
    return {
      url: "",
      result: Object,
      records: Object,
      searched: false,
      recorded: false
    };
  },
  methods: {
    search: function() {
      if (!this.url.length) {
        alert("The host name to search is empty");
        return;
      }
      fetch("http://10.64.0.9:3000/check/" + this.url)
        .then(response => response.json())
        .then(json => {
          this.result = json;
          this.recorded = false;
          this.searched = true;
        });
    },
    record: function() {
      fetch("http://10.64.0.9:3000/domain")
        .then(response => response.json())
        .then(json => {
          this.records = json;
          this.recorded = true;
          this.searched = false;
        });
    }
  }
};
</script>

<style scoped>
</style>