<template>
    <h1 class="mb-3 text-2xl font-bold">ToDoList</h1>
  <form @submit.prevent="newAddItem">
    <label class="mr-2 text-green-600" for="text">write here:</label>
    <input 
    class="mr-2 border-double border-4 border-light-blue-500" type="text" placeholder="ここに入力" 
    v-model="newText"/>
    <button 
    class="button bg-green-400 px-2 py-1 rounded text-white"
    >追加</button>
  </form>
  <ul v-if="items.length" class="mt-4">
    <Foo v-for="(item, index) in items"
     :key="item.id"
     :item="item"
     @delete="items.splice(index, 1)"
     />
  </ul>
  <p class="mt-4" v-else>no Item</p>
</template>

<script>
// imported components are also directly usable in template
import Foo from './components/Foo.vue'

export default{
  name: 'App',
  components: {
    Foo
  },
  data(){
    return{
      newText: '',
      items: [
        {id: 1, title: 'toDoItem'},
      ],
      nextId: 2
    }
  },
  methods: {
    newAddItem(){
      const trimmedItem = this.newText.trim()
      if( trimmedItem ){
        this.items.push({id: this.nextId++,title: this.newText })
      }
      this.newText = ''
    }
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

</style>