<template>
  <div class="home">
    <div id="list-complete-demo" class="demo">
      <b-button variant="primary" v-on:click="add">Add</b-button>
      <b-button variant="danger" v-on:click="remove">Remove</b-button>
      <transition-group name="list-complete" tag="p">
        <span v-for="item in items" v-bind:key="item" class="list-complete-item">{{ item.n }}</span>
      </transition-group>
      <b-form-input v-model="filter" placeholder="Type to Search" />
      <div>
        <b-table striped :items="items" :filter="filter" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  data: function() {
    return {
      items: [
        { "#": 1, n: "abc" },
        { "#": 2, n: "def" }
      ],
      nextNum: 3,
      filter: null
    };
  },
  methods: {
    randomIndex: function() {
      return Math.floor(Math.random() * this.items.length);
    },
    randomAphabet: function() {
      var chars = "abcdefghijklmnopqrstuvwxyz";
      return chars.charAt(Math.floor(Math.random() * chars.length));
    },
    add: function() {
      this.items.splice(this.randomIndex(), 0, {
        "#": this.nextNum++,
        n: this.randomAphabet() + this.randomAphabet() + this.randomAphabet()
      });
    },
    remove: function() {
      this.items.splice(this.randomIndex(), 1);
    }
  }
};
</script>

<style>
.list-complete-item {
  transition: all 1s;
  display: inline-block;
  margin-right: 10px;
}
.list-complete-enter,
.list-complete-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
.list-complete-leave-active {
  position: absolute;
}
</style>


<!-- 
<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  }
};
</script>
-->