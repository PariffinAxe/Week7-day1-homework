<template>
  <div id="app">
    <form v-on:submit.prevent="saveNewItem(picked)">
      <label for="new-item">Add To Do Item</label>
      <input type="text" id="new-item"
      v-model="newItem">
      <label for="High">High</label>
      <input type="radio" name="priority" v-model="picked" value="High">
      <label for="Low">Low</label>
      <input type="radio" name="priority" v-model="picked" value="Low">
      <input type="submit" value="Save Item">
    </form>
    <ul>
      <li v-for="(item, index) in list" :class="item.priority==='High' ? 'High' : 'Low'" :key="index">
        <p>{{ item.description }}</p>
        <p v-if="item.priority==='High'">High Priority</p>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  data(){
    return {
      list: [
        {description: "Buy Shopping", priority: "Low"},
        {description: "Clean Bathroom", priority: "Low"},
        {description: "Car's MOT", priority: "High"},
      ],
      newItem: "",
      picked: "",
    }
  },
  methods: {
    saveNewItem: function(picked){
      this.list.push(
        {description: this.newItem, priority:picked}
      ),
      this.newItem = "",
      this.picked = ""
    },
  }

  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul {
  list-style-type: none;
}

li {
  margin: 2px;
  display: flex;
  border: solid 3px;
  justify-content: space-around;
}

li.High {
  border-color: red;
}

li.Low {
  border-color: black;
}
</style>
