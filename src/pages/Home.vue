<template>
  <div id="home">
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h1 class="bg-warning p-4 ">Bitfumes Tutorial</h1>
          <p :class="bgColor">Class Binding</p>
          <p :class="{'alert alert-success': isActive, 'col-12': isMin}" :style="styleSection" :title="title">Style
            Binding</p>
<!--          :style="['test' === className ? {background:blog.color}: '', index === 0 && show ? {background:blog.color}: '']"-->
          <p :class="[isActive ? 'alert alert-info' : 'alert alert-danger']">
            Condition class Binding</p>
          <p class="bg-secondary">Method & computed</p>
          <div class="row">
            <div class="col-4">
              <h4> computed </h4>
              <h4> {{ reverseC }}</h4>
              <h4>{{ reverseC }}</h4>
              <h4>{{ reverseC }}</h4>
              <h4>{{ reverseC }}</h4>
            </div>
            <div class="col-4">
              <h4> Method </h4>
              <h4> {{ reverse() }}</h4>
              <h4>{{ reverse() }}</h4>
              <h4>{{ reverse() }}</h4>
              <h4>{{ reverse() }}</h4>
            </div>
          </div>
          <p class="bg-info">Watch</p>
          <input type="number" v-model="km">
          <input type="number" v-model="m">
          <p class="bg-primary mt-2">Getter</p>
          <input type="text" class="form-control" v-model="fullName">
          <h4>{{ firstName }}</h4>
          <h4>{{ lastName }}</h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Home",

  data() {
    return {
      isActive: true,
      isMin: true,
      bgColor: 'bg-success p-2',
      styleSection: {
        border: '1px solid blue',
        textAlign: 'center'
      },
      title: "This is title",
      message: 'This is VueJs',
      km: 0,
      m: 0,
      firstName: "Hello",
      lastName: "World"
    }
  },

  methods: {
    reverse() {
      return Date.now()
    }
  },
  computed: {
    reverseC() {
      return Date.now()
    },
    fullName: {
      get: function () {
        return this.firstName + ' ' + this.lastName;
      },
      set: function (valueInput) {
        var valueInput = valueInput.split(' ');
        this.firstName = valueInput[0];
        this.lastName = valueInput[value.length - 1];

      }
    }
  },

  watch: {
    km: function (val) {
      this.km = val
      this.m = val * 1000
    },
    m: function (val) {
      this.m = val
      this.km = val / 1000
    }
  }


}
</script>
