<template>
  <div id="app">
<!--    <Home/>-->
<!--    <Event/>-->
<!--    <propes/>-->
    <FormValidation/>

  </div>
</template>

<script>

import Home from "./pages/Home";
import Event from "./pages/Event"
// import Propes from "./pages/Propes";
import FormValidation from "./pages/FormValidation";

export default {
  name: 'App',
  components:{
    FormValidation,
    // Propes,
    // Home,
    // Event,
  }

}
</script>
