<template>
  <div id="app">
    <p>Raw Data</p>
    <textarea v-model="rawData" placeholder=""></textarea>
    <p>Found Codes:</p>
    <p>{{ codes.sort().join(",") }}</p>
  </div>
</template>

<script>
export default {
  name: "App",
  computed: {
    codes() {
      if (this.rawData.length == 0) return [];
      const codes = this.rawData.match(/(FRIEND-\w*)|(THANKS-\w*)/g);
      return [...new Set(codes)];
    },
  },
  data() {
    return {
      rawData: "",
    };
  },
};
</script>
