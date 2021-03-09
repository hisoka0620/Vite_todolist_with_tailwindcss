<template>
  <div class="edit-wrapper flex flex-col justify-center">
    <div>
      <input type="text"
      class="mr-2 border-double border-4 border-light-blue-500"
      v-model="item.title"
      />
    </div>
    <div class="p-2">
      <button
      class="button bg-yellow-400 px-2 py-1 rounded ml-2 text-white"
      @click="editSwitch"
      >キャンセル</button>
      <button
      class="button bg-blue-400 px-2 py-1 rounded ml-2 text-white"
      @click="stateSave"
      >保存</button>
    </div>
  </div>
</template>

<script>
export default{
  name: 'Edit',
  props: ['item'],
  data(){
    return{
      show: true
    }
  },
  methods: {
    editSwitch(){
      this.$emit('editCancel')
    },
    stateSave(){
      this.$emit('editSave')
    }
  }
}
</script>

<style scoped>

</style>