<template>
  <div class="home">
    <Calculator msg="Calculator" />
  </div>
</template>

<script>
// @ is an alias to /src
import Calculator from "@/components/CalculatorView.vue";

export default {
  name: "HomeView",
  components: {
    Calculator,
  },
};
</script>
