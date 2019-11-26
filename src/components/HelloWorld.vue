<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <div>
      <label for="">この数値以上のリストアイテムを表示する</label>
      <input type="number" v-model="inputNumber">
    </div>

    <div>
      <draggable v-model="list" v-on:update="onUpdate">
        <div
          v-for="(item, index) in list" v-bind:key="index"
          v-bind:style="listItemStyle"
          v-show="item.level >= inputNumber">
          {{item.name}}
        </div>
      </draggable>
    </div>

    <div>以下、別のコンポーネント</div>

    <div>
      <draggable v-model="list" v-on:update="onUpdate">
        <ListItem
          v-for="(item, index) in list" v-bind:key="index"
          v-bind:style="listItemStyle"
          v-show="item.level >= inputNumber"
          v-bind:item="item">
        </ListItem>
      </draggable>
    </div>
  </div>
</template>

<script>
//
import draggable from 'vuedraggable'
import ListItem from '@/components/ListItem.vue'

export default {
  name: 'HelloWorld',
  components : {
    draggable,
    ListItem
  },
  data : function() {
    return {
      msg: 'Welcome to Your Vue.js App',
      list : [
        {name : "sample1", level : 1},
        {name : "sample2", level : 2},
        {name : "sample3", level : 3},
        {name : "sample4", level : 4},
        {name : "sample5", level : 5},
        {name : "sample6", level : 6},
        {name : "sample7", level : 7},
        {name : "sample8", level : 8},
        {name : "sample9", level : 9},
        {name : "sample10", level : 10},
      ],
      listItemStyle : {
        margin : "auto",
        width : "10%",
        border : "1px solid black"
      },
      inputNumber : 0
    }
  },
  watch : {
    list : function(new_value, old_value) {
      console.log("old", old_value);
      console.log("new", new_value);
    }
  },
  methods : {
    onUpdate : function() {
      console.log("Update");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
