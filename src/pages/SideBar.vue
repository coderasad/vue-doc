<template>
    <div class="row">
      <div class="col-4">
        <ul class="list-group">
          <li class="btn-danger px-3 py-2">{{ $parent.value }}</li>
          <li @click="active = index" :class="{active: active === index }" class="list-group-item" v-for="(menu, index) in menus" :key="index">{{menu}}</li>
        </ul>
        <a class="btn btn-warning mt-2 mb-2">{{ index }}</a>
      </div>
    </div>
</template>

<script>
export default {
  name: "SideBar",

  data() {
    return {
      index: 10,
      menus: [
        "Home",
        "About",
        "Blog",
        "Contact",
      ],
      active: 0
    }
  },
  mounted() {
    setTimeout(()=>{
      this.index ++
    }, 5000)

  },




}
</script>

