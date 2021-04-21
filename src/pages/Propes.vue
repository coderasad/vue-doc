<template>
  <div id="props">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <h4 class="bg-secondary p-3 text-center">Props & Set Time out</h4>
          <a class="btn btn-success mb-2" @click="increment">Add</a>
        </div>
      </div>
      <SideBar ref="sideBar"/>
      <span class="btn btn-danger">{{value}}</span>
    </div>
  </div>
</template>

<script>

import SideBar from "./SideBar";

export default {
  name: "Propes",

  components: {
    SideBar
  },

  data() {
    return {
      value: 0,
    }
  },

  methods: {
    increment() {
      this.value += 1;
    }
  }
}
</script>
