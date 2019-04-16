<template>
  <div id="app">
    <div>
      <h1>{{heading}}</h1>
      <input type="text" v-model="info" />
      <button @click="handleClick">Add</button>
    </div>
    <ul>
      <todo-item  v-for="(item,index) in list" :key="index">
        <template v-slot:item="itemProps">
          <span :style="{fontSize:'20px', color:itemProps.checked?'red':'blue'}">{{item}}</span>
        </template>
      </todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'app',
  components: {
    'todo-item': TodoItem
  },
  data() {
		return {
      heading: "Todo list",
			info: "",
			list: []
		};
	},
	methods: {
		handleClick() {
			this.list.push(this.info);
			this.info = "";
		}
	}
}
</script>

<style>

</style>
