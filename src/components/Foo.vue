<template>
  <li v-if="isEditing" class="mb-3">
      {{ item.title }}
    <button 
    class="button bg-red-400 px-2 py-1 rounded ml-2 text-white"
    @click="$emit('delete')"
    >削除</button>
    <button
    class="button bg-yellow-400 px-2 py-1 rounded ml-2 text-white"
    @click="edit"
    >編集</button>
  </li>
  <Edit v-else @editCancel="editCanceled" @editSave="editStateSave" :item="item"/>
</template>

<script>
import Edit from './Edit.vue'

export default{
  name: 'Foo',
  props: ['item'],
  components: {
    Edit
  },
  data(){
    return{
      isEditing: true,
    }
  },
  methods: {
    edit(){
      this.isEditing = false 
    },
    editCanceled(){
      this.isEditing = true
    },
    editStateSave(){
      this.isEditing = true
    }
  }
}

</script>

<style scoped>
a {
  color: #42b983;
}
</style>