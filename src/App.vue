<script setup>
import { ref } from 'vue'
import draggable from 'vuedraggable' // <-- Import ini

const lists = ref([
  { id: 1, title: 'Ideas', cards: [
    { id: 101, text: 'Beli Ceri' },
    { id: 102, text: 'Moodboard Cherry Task' }
  ], isAdding: false, newTask: '' },
  { id: 2, title: 'In Progress', cards: [
    { id: 201, text: 'Coding UI' }
  ], isAdding: false, newTask: '' },
  { id: 3, title: 'Finished', cards: [
    { id: 301, text: 'Setup Vite' }
  ], isAdding: false, newTask: '' }
])

const addCard = (list) => {
  if (list.newTask.trim() !== '') {
    // Kita pakai object supaya draggable lebih stabil
    list.cards.push({ id: Date.now(), text: list.newTask })
    list.newTask = ''
    list.isAdding = false
  }
}
</script>

<template>
  <div class="min-h-screen bg-cosmic p-8 font-sans">
    
    <header class="mb-12 flex items-center justify-center gap-3">
      <div class="w-10 h-10 bg-sangria rounded-full shadow-lg"></div> 
      <h1 class="text-4xl font-extrabold text-sangria tracking-tighter">CHERRY TASK</h1>
    </header>

    <main class="flex gap-6 overflow-x-auto pb-10 items-start">
      <div v-for="list in lists" :key="list.id" 
           class="bg-white w-80 shrink-0 rounded-3xl shadow-xl overflow-hidden border border-gray-100">
        
        <div class="bg-cornflower p-4">
          <h2 class="font-black text-white uppercase text-sm tracking-widest">{{ list.title }}</h2>
        </div>

        <div class="p-5">
          <draggable 
            v-model="list.cards" 
            group="tasks" 
            item-key="id"
            ghost-class="opacity-50"
            drag-class="rotate-3"
            class="space-y-4 min-h-[50px]"
          >
            <template #item="{ element }">
              <div class="bg-cosmic p-4 rounded-2xl border-l-4 border-sangria shadow-sm text-gray-800 font-medium cursor-grab active:cursor-grabbing">
                {{ element.text }}
              </div>
            </template>
          </draggable>

          <div v-if="list.isAdding" class="mt-4">
            <textarea v-model="list.newTask" 
                      placeholder="Apa rencanamu?" 
                      class="w-full p-3 rounded-2xl border-2 border-cornflower focus:outline-none text-sm"
                      rows="2"></textarea>
            <div class="flex gap-2 mt-2">
              <button @click="addCard(list)" class="bg-sangria text-white px-5 py-2 rounded-xl text-xs font-bold uppercase">Tambah</button>
              <button @click="list.isAdding = false" class="text-gray-400 text-xs font-bold uppercase">Batal</button>
            </div>
          </div>

          <button v-else @click="list.isAdding = true" 
                  class="mt-6 w-full py-3 text-xs font-black uppercase text-cornflower border-2 border-dashed border-cornflower/30 rounded-2xl hover:bg-cornflower/5 transition">
            + New Task
          </button>
        </div>
      </div>
    </main>
  </div>
</template>