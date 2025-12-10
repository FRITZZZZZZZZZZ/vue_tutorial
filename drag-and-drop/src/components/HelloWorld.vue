<template>
  <div
    class="drop-zone"
    @drop="onDrop($event, 1)"
    @dragenter.prevent
    @dragover.prevent
    >
    <div
      v-for="item in getList(1)"
      :key="item.id"
      class="drag-el"
      draggable="true"
      @dragstart="startDrag($event, item)"
    >
      {{ item.title }}
    </div>
  </div>
  <div
    class="drop-zone"
    @drop="onDrop($event, 2)"
    @dragenter.prevent
    @dragover.prevent
  >
    <div
      v-for="item in getList(2)"
      :key="item.id"
      class="drag-el"
      draggable="true"
      @dragstart="startDrag($event, item)"
    >
      {{ item.title }}
    </div>
  </div>
</template>

<script> 
import { ref } from 'vue'

export default {
  setup() {
    const items = ref([
      { id: 0, title: 'Item A', list: 1 },
      { id: 1, title: 'Item B', list: 1 },
      { id: 2, title: 'Item C', list: 2 },
    ])

    const getList = (list) => {
      return item.value.filter((item) => item.list == list)
    }

    const startDrag = (event, item) => {
      console.log(item)
      event.dataTransfer.setData('itemID', item.id)
    }

    return {
      getList,
      startDrag,
    }
  }
}
</script>

<style>
  
</style>