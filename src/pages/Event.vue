<template>
  <div id="event">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <h1 class="bg-warning p-4 ">Bitfumes Tutorial</h1>
          <p class="bg-secondary text-center">Best example of Events</p>
          <div class="row">
            <div class="col-4">
              <ul class="list-group">
                <li @click="addFruit(fruit)" v-for="(fruit, index)  in fruits" :key="index"
                    :class="fruit.class" class="list-group-item d-flex justify-content-between align-items-center">
                  {{ fruit.name }}
                  <span class="badge bg-info badge-pill">{{ fruit.cost }}</span>
                </li>
                <li class="list-group-item">{{ total }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Event",

  data() {
    return {
      isTrue: true,
      fruits: [
        {name: 'Apple', cost: 10, clicked: false, class: 'unselect'},
        {name: 'Orange', cost: 20, clicked: false, class: 'unselect'},
        {name: 'Banana', cost: 30, clicked: false, class: 'unselect'},
      ],
      total: 0
    }
  },

  methods: {
    addFruit(fruit){
      if(fruit.clicked){
        this.total -= fruit.cost
        fruit.class = 'unselect'
      }else{
        this.total += fruit.cost
        fruit.class = 'select'
      }
        fruit.clicked = !fruit.clicked
    }

  },


}
</script>
<style>
  .select {
    background: #9bbf9a !important;
  }
  .unselect {
    background: #97f631 !important;
  }
</style>
