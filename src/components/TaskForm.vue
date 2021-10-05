<template>
  <form @submit.prevent="addTask">
      <input
      v-model.trim="text"
      type="text"
      placeHolder="New Task"
      class="form-control"
      >
      <button class="btn btn-primary mt-2 w-100">Add Task</button>
  </form>
</template>

<script>
import { inject, ref } from 'vue'

export default {
    setup(){
        const text = ref('')

        //inject Tasks
        const tasks = inject('tasks')

        const addTask = () => {
            if(text.value ===''){
                return console.log("empty")
            }
            const Task = {
                text: text.value,
                state: false,
                id: Date.now()
            }
            tasks.value.push(Task)
            text.value =''
        }

        return {addTask,text}
    }
}
</script>