<template>
  <div class="alert alert-warning mt-3 d-flex justify-content-between align-item-center">
      <p class="m-0" :class="{'lineThrought': task.state}">{{task.text}}</p>
      <div>
          <i 
            class="fas fa-undo-alt mx-2 text-success" 
            role="button"
            @click="editTask(task.id)"
            v-if="task.state"
            ></i>
         <i 
            class="fas fa-check-circle mx-2 text-success" 
            role="button"
            @click="editTask(task.id)"
            v-if="!task.state"
            ></i>   
          <i 
            class="fas fa-minus-circle mx-2 text-danger" 
            role="button"
            @click="deleteTask(task.id)"
          ></i>
      </div>
  </div>
</template>

<script>
import { inject } from 'vue'
export default {
    props: {
        task: {
            type: Object,
            required: true
        }
    },
    setup(){

        //inject tasks
        const tasks = inject('tasks')

        //task events handled from latest component
        const deleteTask = (id) => {
            tasks.value = tasks.value.filter(item => item.id !== id)
        }

        const editTask = (id) => {
            tasks.value = tasks.value.map(item => {
                if(item.id === id){
                    item.state = !item.state
                }
                return item
            })
        }

        return {deleteTask,editTask}
    }

}
</script>
<style scoped>
    .lineThrought{
        text-decoration: line-through;
    }
</style>