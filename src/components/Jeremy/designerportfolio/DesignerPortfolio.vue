<template>
  <div>
    <Mynav/>
    <h1>this is the portfolio page</h1>
    <Myfooter/>
  </div>
</template>

<script>
import Mynav from ".././mynav/Mynav.vue";
import Myfooter from ".././myfooter/Myfooter.vue";

export default {
  name: "DesignerPorfolio",
  components: {
    Mynav,
    Myfooter
  }
};
</script>

<style scoped>
</style>
