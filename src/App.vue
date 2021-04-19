<template>
  <div id="app">
    <FloatingInput :config="config" />
  </div>
</template>

<script>
import FloatingInput from "./components/floating-input";
export default {
  name: "App",
  components: { FloatingInput },
  data() {
    return {
      config: {
        label: "Locality or Landmark",
        id: "addressInput",
        customClass: "",
        valid: "isValid",
      },
    };
  },
};
</script>

<style lang="scss">
#app {
  color: #2c3e50;
}
</style>
