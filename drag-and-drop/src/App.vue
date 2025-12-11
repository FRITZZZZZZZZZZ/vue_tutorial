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
  <div>
    <h1>
      Drop counter
    </h1>
    <p>item A {{ counterA }}</p>
    <p>item B {{ counterB }}</p>
    <p>item C {{ counterC }}</p>
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

    const counterA = ref(0)
    const counterB = ref(0)
    const counterC = ref(0)

    const getList = (list) => {
      return items.value.filter((item) => item.list == list)
    }

    const startDrag = (event, item) => {
      console.log(item)
      event.dataTransfer.setData('title', item.title)
    }

    const onDrop = (event, list) => {
      const itemTitle = event.dataTransfer.getData('title')
      switch(itemTitle) {
        case 'Item A':
          counterA.value++;
          break;
        case 'Item B':
          counterB.value++
          break;
        case 'Item C':
          counterC.value++
          break;
      }
    }

    return {
      getList,
      startDrag,
      onDrop,
      counterA,
      counterB,
      counterC
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  margin-top: 60px;
}

.drop-zone { 
  width: 50%;
  margin: 50px auto;
  background-color: green;
  pad: 10px;
  min-height: 10px;
}

.drag-el {
  background-color: blue;
  color: white;
  padding: 5px;
  margin-bottom: 10px;
}

.drag-el:nth-last-of-type(1) {
  margin-bottom: 0;
}
</style>