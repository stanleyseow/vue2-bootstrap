<template>
  <div id="app">
    <h2 class="greenFont">My first ever Vue Tutorial</h2>

    <h4 class="blueFont">{{ message }}</h4>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      message: "Hello",
    };
  },
  methods: {},
  computed: {},
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}

.blueFont {
  color: blue;
}

.greenFont {
  color: green;
}
.redbg {
  background: red;
}
</style>
